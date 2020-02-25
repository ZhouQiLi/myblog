当有两个uint32类型表示高低位的字段需要合成一个uint64类型时

    uint32_t lo = 1;
    uint32_t hi = 2;    
    uint64_t num = static_cast<uint64_t>(lo) | static_cast<uint64_t>(hi) << 32;

Clang-Tidy可能会有以下报错:

![avatar]("images/page1.png")

意思是对有符号数做位操作, 因为Clang-Tidy的静态检查比较严谨, 位操作数必须是无符号数, 包括常量。所以32要改成32U。