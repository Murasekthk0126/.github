---
name: architecture-guide
description: 新機能実装時、コンポーネント作成時、APIエンドポイント追加時に使用。レイヤー構造遵守、既存パターン調査。
allowed-tools: Read, Grep, Glob
---
# アーキテクチャガイド
## 実装手順
1. Grepで既存の類似機能を検索
   Grep('FeatureName', 'src/')
2. Readで既存実装を確認
   - サービス層の呼び出し方
   - エラーハンドリングのパターン
   - テストの書き方
3. パターンに従って実装
4. Bashでテストを実行

## サービス層の呼び出しパターン
// 推奨パターン
try {
  const result = await service.method();
} catch (error) {
  logger.error(error);
  throw new ApplicationError(error);
}

## ルール
- UIレイヤーはサービス層を経由すること
- 新しいコンポーネントを作る前に、Grepで既存パターンを検索すること
- architecture.mdのレイヤー構造を遵守すること
