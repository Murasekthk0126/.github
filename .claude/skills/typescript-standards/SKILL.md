---
name: typescript-standards
description: TypeScript開発の規約とベストプラクティス。TypeScriptコード作成時、型定義時に使用。型の命名規則、非同期関数の型定義、ジェネリクスの使用パターンを定義。
allowed-tools: Read, Grep, Glob
---
# TypeScript開発規約
## 型定義のルール
### 新しい型を定義する前に
**必ず**Grepツールで既存の類似型を検索してください：
Grep('User', 'src/types/')
見つかった既存の型定義をReadツールで読み、以下の点を確認：
- 命名規則（例：'UserProfile'、'UserSettings'）
- 必須プロパティとオプショナルプロパティの使い分け
- ジェネリクスの使用パターン

### 型の命名規則
// 良い例
interface User { id: string; name: string; }
interface UserProfile { bio: string; avatar: string; }
// 悪い例
interface Data { value: string; } // × 何のデータか不明確

### 非同期関数の型定義
// 良い例
async function fetchUser(id: string): Promise<User> {
  const response = await api.get(`/users/${id}`);
  return response.data;
}
// 悪い例（禁止）
async function fetchUser(id: string) { // × 戻り値の型が不明確

## 詳細情報
TypeScriptのベストプラクティス詳細については ./best-practices.md を参照。
