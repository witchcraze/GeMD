# GEMINI.md: AI駆動開発のための指示書

このドキュメントは、AIアシスタント（Gemini）がGeMDプロジェクトにおいて開発タスクを遂行するための指示書です。一貫性、品質、効率性を担保するため、以下のガイドラインに厳密に従ってください。

## 1. 本ドキュメント(GEMINI.md)の運用指針

### 1.1. 目的
このドキュメントは、AIが自律的に開発を進めるための「思考と行動の起点」です。AIへの指示はすべてここに集約され、プロジェクトの憲法として機能します。

### 1.2. 構成と記述ルール
本ドキュメントの肥大化を防ぎ、可読性とメンテナンス性を維持するため、以下のルールに従って記述します。

*   **戦略とワークフローの明確な分離:**
    *   **戦略セクション (3章):** プロジェクトが **「何を (What)」** 目指し、 **「なぜ (Why)」** そうするのかという **方針** のみを記述します。長期的で普遍的な指針が対象です。
    *   **ワークフローセクション (4章):** 戦略を実現するために **「どのように (How)」** 作業するのかという、**具体的で再現可能な手順** のみを記述します。AIが直接実行・参照するコマンドや規約が対象です。
*   **詳細の外部化:**
    *   特定の技術に関する詳細なセットアップ手順、設計思想、長文の規約などは、`docs/`ディレクトリ配下に別のMarkdownファイルとして作成します。
    *   本ドキュメントには、その外部ファイルへの参照（リンク）を記述するに留め、本文書はAIの行動を規定する「指示」に特化させます。

### 1.3. 更新プロセス
本ドキュメントの変更は、品質を維持し、意図しない変更を防ぐため、以下のプロセスを必須とします。
1.  GitHub Issueで変更を提案します。
2.  提案が承認された後、AIがこのドキュメントを更新するPull Requestを作成します。
3.  Pull Requestがレビューされ、マージされることで変更が確定します。

### 1.4. 記述スタイルガイド
本ドキュメントの可読性を維持するため、以下の記述スタイルに従います。

*   **箇条書き（リスト）の使用:**
    *   **目的:** 手順、チェックリスト、並列な選択肢など、順序や階層を持つ情報を記述する場合に使用します。
    *   **例:** 開発プロセスのステップ、セルフレビューの観点。

*   **表（テーブル）の使用:**
    *   **目的:** 複数の項目を、共通の属性で比較・対照する場合に使用します。情報の対応関係を明確に示したい場合に最適です。
    *   **例:** ラベル一覧とそれぞれの役割、コマンドのオプションと説明。

*   **文体:** AIへの指示であることが明確になるよう、敬体（です・ます調）ではなく、常体（だ・である調）または命令形で記述します。

---

## 2. AI連携における基本原則
*   **目的志向:** Issueに書かれた表面的な指示だけでなく、その背後にあるユーザーの最終的な目的を理解し、目標達成のために能動的に行動してください。
*   **規約の遵守:** 本リポジトリで定められたコーディングスタイル、テストフレームワーク、アーキテクチャパターンに厳密に従ってください。
*   **透明性の確保:** ファイル変更やコマンド実行など、AIが行った操作はすべて明確に記録・報告してください。
*   **段階的な実行:** 大きな変更は小さなステップに分割し、重要な判断が必要な場面では必ずユーザーに確認を求めて���ださい。

## 3. プロジェクト戦略
*(このセクションでは、プロジェクトが目指す「方針」のみを記述します)*

*   **開発戦略:** (今後定義：例：テスト駆動開発を基本とし、コードの品質と保守性を最優先する)
*   **GitHub運用戦略:** (今後定義：例：GitHub Flowを採用し、mainブランチが常にデプロイ可能な状態を維持することで、迅速な価値提供を目指す)

## 4. 開発ワークフロー
*(このセクションでは、戦略を実行するための「具体的で再現可能な手順」のみを記述します。AIはこのワークフローに厳密に従って、自律的に開発を遂行します)*

### 4.1. 基本原則：シングルタスクの徹底
AIは、複数のIssueを同時に処理しません。必ず一つのIssueが完了（マージ）してから、次のIssueに着手します。これにより、ブランチのコンフリクトや作業の混乱を防ぎます。

### 4.2. Issue駆動開発プロセス
以下は、一つのIssueが起票されてからクローズされるまでの一連のプロセスです。AIとユーザーはこのプロセスに従って連携します。

#### **ステップ1: Issueの受付と担当設定**
1.  **トリガー:** ユーザーまたはAIが新しいIssueを作成���ます。
2.  **AIの対応:**
    *   AIは新しく作成されたIssueを検知し、自身をそのIssueの担当者（Assignee）として設定します。
    *   Issueの内容を分析し、`4.4. ラベル管理`で定義された**状態ラベル**と**種別ラベル**の中から、最も適切と思われるラベルを付与します。
        *   **状態ラベル:** `status: planning`
        *   **種別ラベル:** `type: feature` や `type: bug` などから1つを選択

#### **ステップ2: 実装計画の策定と合意形成**
1.  **トリガー:** Issueに `status: planning` ラベルが付与される。
2.  **AIの対応:**
    *   Issueの内容と、`docs/`配下の関連ドキュメントをすべて読み込み、目的と背景を完全に理解します。
    *   理解した内容に基づき、実装や仕様変更に伴って更新が必要なドキュメントとコードを特定します。
    *   実現に必要なタスク（コード変更、ドキュメント更新など）を分解し、変更予定のファイルをすべてリストアップした、具体的な実装計画を立てます。
    *   以下のフォーマットで、実装計画をIssueにコメントします。その際、本文の長短に関わらず、必ず一時ファイルを作成し`--body-file`オプションを使��します。
        ```markdown
        ### 実装計画のご提案

        このIssueを解決するため、以下の計画で実装を進めます。

        **変更対象ファイル:**
        - `docs/01_ARCHITECTURE.md`
        - `src/core/main.py`
        - `tests/test_main.py`

        #### 1. **(ドキュメント更新の概要)**
        - `docs/01_ARCHITECTURE.md`: (更新内容の要約)

        #### 2. **(コード変更の概要)**
        - `src/core/main.py`: (具体的な作業内容 a)
        - `tests/test_main.py`: (具体的な作業内容 b)

        ---
        ご承認いただける場合は、このコメントに「承認」と返信してください。
        ```
3.  **ユーザーの対応:**
    *   計画をレビューし、問題がなければ「承認」とコメントします。修正が必要な場合は、具体的な修正点を指示します。

#### **ステップ3: 実装とPull Requestの作成**
1.  **トリガー:** ユーザーが実装計画を「承認」する。
2.  **AIの対応:**
    *   Issueの `status: planning` ラベルを削除し、`status: implementing` ラベルを付与します。
    *   `main` ブランチから、`{issue番号}-{issueのタイトルをケバブケースにしたもの}` という命名規則で新しいブランチを作成します。
        *   例: `12-update-development-workflow`
    *   実装計画に沿って、コードの変更、ファイルの作成・編集、テストの追加などを行います。
        *   **【重要】計画外のファイル変更の原則禁止:** AIは、実装計画で合意されたファイル以外は原則として変更しません。もし実装の過程で、計画外のファイル変更が必要だと判断した場合は、作業を中断し、その理由と変更内容をユーザーに報告し、承認を求めます。
    *   作業が完了したら、変更内容をコミットします。コミットメッセージは [Conventional Commits](https://www.conventionalcommits.org/) の規約に従います。
    *   `main` ブランチをターゲットにしたPull Requestを作成します。
    *   PRの本文には、関連するIssueへのリンク（例: `Closes #12`）を必ず含めます。

#### **ステップ4: セルフレビューとPRのレビュー依頼**
1.  **トリガー:** Pull Requestが作成される。
2.  **AIの対応:**
    *   Issueの `status: implementing` ラベルを削除し、`status: review` ラベルを付与します。
    *   PR上で、AI自身によるセルフレビューを実施します。以下の観点で確認し、その結果をPRにコメントします。その���、本文の長短に関わらず、必ず一時ファイルを作成し`--body-file`オプションを使用します。
        ```markdown
        ### セルフレビュー報告

        以下の観点でセルフレビューを実施しました。

        - **[観点1] 実装はIssueの要求を満たしているか？**
          - (確認結果と自己評価)
        - **[観点2] `GEMINI.md`の規約（テスト、命名規則など）を遵守しているか？**
          - (確認結果と自己評価)
        - **[観点3] コードは十分に読みやすく、保守性が高いか？**
          - (確認結果と自己評価)
        - **[観点4] 変更による潜在的な副作用はないか？**
          - (確認結果と自己評価)

        ---
        ご確認の上、マージのご承認をお願いいたします。
        ```
3.  **ユーザーの対応:**
    *   PRの内容とAIのセルフレビューをレビューします。
    *   問題がなければ、PRに対して「マージを承認します」とコメントします。修正が必要な場合は、具体的な修正点をコメントします。

#### **ステップ5: マージとクリーンアップ**
1.  **トリガー:** ユーザーがPull Requestに「マージを承認します」とコメントする。
2.  **AIの対応:**
    *   Pull Requestをマージします。
    *   作業ブランチを削除します。
    *   関連するIssueが自動でクローズされたことを確認します。（PRの `Closes #12` により自動化）

### 4.3. テストワークフロー
*   **テスト実行コマンド:** (今後定義)
*   **テストファイルの命名規則:** (今後定義)

### 4.4. ラベル管理
AIは、IssueやPull Requestの状況と種類を明確にするため、以下のラベルを使用します。
AIは、ラベルを付与する際に該当のラベルが存在しない場合、以下の定義に従って自動でラベルを作成した上で付与します。

#### **状態ラベル (Status)**
IssueやPRが現在どの開発段階にあるかを示します。

| ラベル名 | 色 | 説明 |
| :--- | :--- | :--- |
| `status: planning` | `#FBCA04` | AIが実装計画を策定中の状態 |
| `status: implementing` | `#1D76DB` | AIが実装作業中の状態 |
| `status: review` | `#8E44AD` | Pull Requestがレビュー待ちの状態 |

#### **種別ラベル (Type)**
IssueやPRがどのような種類のタスクであるかを示します。

| ラベル名 | 色 | 説明 |
| :--- | :--- | :--- |
| `type: bug` | `#D73A4A` | 既存機能の不具合 |
| `type: feature` | `#0E8A16` | 新しい機能の追加 |
| `type: documentation` | `#0075CA` | ドキュメントの作成・更新 |
| `type: refactor` | `#A2EEEF` | 外部的な振る舞いを変更しないコード改善 |
| `type: chore` | `#FFFFFF` | ビルドプロセスや補助ツールの変更など、上記以外のタスク |

## 5. ドキュメント管理ワークフロー
AIがプロジェクトの仕様や設計思想を正確に理解し、開発とドキュメントの整合性を維持するためのワークフローを定義します。

### 5.1. ドキュメントの構成
プロジェクトに関する情報は、`docs/`ディレクトリ配下に以下のファイル群で管理します。AIは開発に着手する前に、必ずこれらのドキュメントに目を通し、内容を理解します。

| ファイル名 | 目的 |
| :--- | :--- |
| `00_PROJECT_OVERVIEW.md` | プロジェクトの全体像と目的を定義する |
| `01_ARCHITECTURE.md` | システムの構造や設計思想を定義する |
| `02_CODING_STANDARDS.md` | コードの一貫性を保つための規約を定義する |
| `03_TESTING_GUIDELINES.md` | 品質を保証するためのテスト方針と手順を定義する |
| `04_SETUP.md` | 開発環境の構築手順を定義する |

### 5.2. ドキュメントの更新プロセス
*   **タイミング:** Issueに対応する実装や仕様変更によって、上記のドキュメントの内容に影響が出る場合に更新します。
*   **手順:**
    1.  AIは、`ステップ2: 実装計画の策定と合意形成`の段階で、更新が必要なドキュメントを特定し、その更新内容を実装計画に含めます。
    2.  ユーザーの承認後、AIはコードの変更と合わせてドキュメントの更新も行います。
*   **`README.md`の管理:** `README.md`はプロジェクトの顔であるため、特に重要な更新があった場合に、他のドキュメント更新と同様のプロセスで更新します。
