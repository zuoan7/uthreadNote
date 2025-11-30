## 数据结构
```
#include <ucontext.h>

typedef struct ucontext_t {
    struct ucontext_t *uc_link;     // 当前上下文结束时恢复的上下文
    sigset_t          uc_sigmask;   // 信号掩码
    stack_t           uc_stack;     // 栈信息
    mcontext_t        uc_mcontext;  // 机器特定的寄存器状态
    // ... 其他实现相关的字段
} ucontext_t;
```
## 函数
```
// 获取当前上下文并保存到 ucp 中
int getcontext(ucontext_t *ucp);

// 设置当前上下文为 ucp 所保存的上下文
int setcontext(const ucontext_t *ucp);

// 创建一个新的上下文，修改 ucp 使其执行 func 函数
void makecontext(ucontext_t *ucp, void (*func)(), int argc, ...);

// 保存当前上下文到 oucp，并切换到 ucp 所保存的上下文
int swapcontext(ucontext_t *oucp, const ucontext_t *ucp);
```
