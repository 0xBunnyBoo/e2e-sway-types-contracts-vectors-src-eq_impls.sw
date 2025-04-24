
Original file line number	Diff line number	Diff line change
@@ -11,13 +11,14 @@ enum TestEnum {
    VariantTwo: (),
}

impl Eq for TestStruct {
impl PartialEq for TestStruct {
    fn eq(self, other: Self) -> bool {
        self.field_1 == other.field_1 && self.field_2 == other.field_2
    }
}
impl Eq for TestStruct {}

impl Eq for TestEnum {
impl PartialEq for TestEnum {
    fn eq(self, other: Self) -> bool {
        match (self, other) {
            (TestEnum::VariantOne, TestEnum::VariantOne) => true,
@@ -26,6 +27,7 @@ impl Eq for TestEnum {
        }
    }
}
impl Eq for TestEnum {}

abi TestContract {
    fn assert_primitive(a: u64, b: u64);
