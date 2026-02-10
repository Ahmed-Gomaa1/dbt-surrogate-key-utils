-- Test data for surrogate key trim functionality
-- This would typically be in a seeds folder in a full dbt project
-- For the package, we'll provide this as example test data

-- Example test case 1: Basic functionality
-- Input: ['a', 'b', 'c'] with trim=false should work as original
-- Input: ['  a  ', '  b  ', '  c  '] with trim=true should equal ['a', 'b', 'c'] with trim=true

-- Example test case 2: Whitespace handling
-- Values with leading/trailing spaces should produce same hash when trim=true
-- Values with leading/trailing spaces should produce different hash when trim=false