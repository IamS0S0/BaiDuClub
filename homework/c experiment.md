# c语言实验
#include <stdio.h>
#include <stdbool.h>
#include <ctype.h>

int main() {
    int ch;            // 用于存储读取的字符
    int char_count = 0; // 字符数
    int word_count = 0; // 字数
    int line_count = 0; // 行数
    bool in_word = false; // 标记是否在一个单词中

    // 逐个读取字符直到 EOF
    while ((ch = getchar()) != EOF) {
        char_count++; // 每读取一个字符，字符数加一

        // 检查是否为换行符
        if (ch == '\n') {
            line_count++; // 行数加一
        }

        // 检查是否为空白符
        if (ch == ' ' || ch == '\t' || ch == '\n') {
            in_word = false; // 遇到空白符，标记为不在单词中
        } else {
            // 如果之前不在单词中，现在遇到字符则表示开始一个新单词
            if (!in_word) {
                word_count++; // 字数加一
                in_word = true; // 更新标记
            }
        }
    }

    // 处理最后一行没有换行符的情况
    if (char_count > 0 && (ch == EOF)) {
        line_count++; // 如果有字符，则最后一行也算
    }

    // 输出统计结果
    printf("字符数: %d\n", char_count);
    printf("字数: %d\n", word_count);
    printf("行数: %d\n", line_count);

    return 0;
}