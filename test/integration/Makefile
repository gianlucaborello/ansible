all: non_destructive destructive check_mode test_hash # amazon rackspace

non_destructive:
	ansible-playbook non_destructive.yml -i inventory -e @integration_config.yml -v $(TEST_FLAGS)

destructive:
	ansible-playbook destructive.yml -i inventory -e @integration_config.yml -v $(TEST_FLAGS)

check_mode:
	ansible-playbook check_mode.yml -i inventory -e @integration_config.yml -v --check $(TEST_FLAGS)

test_hash:
	ANSIBLE_HASH_BEHAVIOUR=replace ansible-playbook test_hash.yml -i inventory -v -e '{"test_hash":{"extra_args":"this is an extra arg"}}'
	ANSIBLE_HASH_BEHAVIOUR=merge ansible-playbook test_hash.yml -i inventory -v -e '{"test_hash":{"extra_args":"this is an extra arg"}}'
