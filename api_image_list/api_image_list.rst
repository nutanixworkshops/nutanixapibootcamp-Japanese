.. _api_image_list:

-----------------
API: イメージの一覧
-----------------

概要
++++++++

この演習ではクラスターのイメージ(仮想マシンになるテンプレート)の一覧を取得します。
後ほど行う演習では得られたレスポンスのJSONに含まれるイメージのUUIDが必要となります。
これらのイメージはAHVのイメージサービスという機能で管理されています。

.. note::

   想定演習時間: **5 分**

演習: クラスタ内イメージ一覧の取得
+++++++++++++++++++++++++++++++++++++++++++

#. Postmanの「+」ボタンをクリックして新しいリクエストのタブを作成します。

#. HTTPメソッドをPOSTにします。

    - Nutanix API v3 ではPOSTメソッドを使ってサーバーサイドのフィルタリング、グルーピング、ソートを実施しています。

#. イメージ一覧を得るためのURLを入力します。

    - https://{{prism_central_ip}}:9440/api/nutanix/v3/images/list

#. ベーシック認証を設定します。設定が残っていれば本手順は飛ばします。

    - **Authorization** タブをクリックし **Basic Auth** をTypeのドロップダウンから選択します。
    - プリズムのクレデンシャルを入力し **Update Request** をクリックします。:
        - **Username** - admin
        - **Password** - 講師から与えられた“Prism login password”を使います。
    - v3 API はHTTPをステートレス(状態がない)なプロトコルとして扱います。そのため、認証はAPIの呼び出しごとに毎回おこなわれます。

#. メディアタイプを「JSON」にします。

        - Bodyタブをクリックします。
        - ラジオボタン(選択ボタン)でrawを選択します。
        - Textのドロップダウンをクリックし、「JSON」を選択します。

#. Bodyにリクエストペイロードの値を記述します。

    - Bodyタブをクリックします。
    - コピーもしくは空データをJSONで記述します。

    .. code-block:: bash

      {}

    .. figure:: images/apimetajson.png

#. Sendボタンを押してv3 APIにリクエストを送信します。

    - レスポンスにはアレイ(リスト)形式でイメージの一覧が表示されます。
    - 「CentOS7.qcow2」というイメージのmetadataにあるUUIDをメモしておきます。

    .. figure:: images/centosuuid.png


    - 「Windows2016.qcow2」というイメージのmetadataにあるUUIDをメモしておきます。

    .. figure:: images/windowsuuid.png
