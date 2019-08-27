---
title: 'Postupy: Ověření DBML a externí soubory mapování'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 212d65dfe998b825dd40e564756083ed685dff6f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041133"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Postupy: Ověření DBML a externí soubory mapování

Externí soubory mapování a soubory. dbml, které upravíte, musí být ověřeny podle příslušných definic schémat. Toto téma poskytuje uživatelům aplikace Visual Studio postupy pro implementaci procesu ověřování.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a>Ověření souboru. dbml nebo XML

1. V nabídce **soubor** v aplikaci Visual Studio přejděte na **otevřít**a potom klikněte na **soubor**.

2. V dialogovém okně **otevřít soubor** klikněte na soubor mapování. dbml nebo XML, který chcete ověřit.

    Soubor se otevře v **editoru XML**.

3. Klikněte pravým tlačítkem na okno a pak klikněte na **vlastnosti**.

4. V okně **vlastnosti** klikněte na tři tečky pro vlastnost **schémata** .

    Otevře se dialogové okno **schémata XML** .

5. Všimněte si vhodné definice schématu pro svůj účel.

    - DbmlSchema. xsd je definice schématu pro ověření souboru. dbml. Další informace naleznete v tématu [generování kódu v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - LinqToSqlMapping. xsd je definice schématu pro ověření externího souboru mapování XML. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

6. Ve sloupci **použít** na požadovaném řádku definice schématu kliknutím otevřete rozevírací seznam a pak klikněte na **použít toto schéma**.

    Definiční soubor schématu je nyní přidružen k vašemu souboru DBML nebo mapování XML.

    Ujistěte se, že nejsou vybrány žádné jiné definice schématu.

7. V nabídce **zobrazení** klikněte na příkaz **Seznam chyb**.

    Určete, zda byly vygenerovány chyby, upozornění nebo zprávy. V takovém případě je soubor XML platný proti definici schématu.

## <a name="alternate-method-for-supplying-schema-definition"></a>Alternativní metoda pro zadání definice schématu

Pokud z nějakého důvodu není příslušný soubor. xsd zobrazen v dialogovém okně **schémat XML** , můžete stáhnout soubor. xsd z tématu nápovědy. Následující kroky vám pomůžou uložit stažený soubor ve formátu Unicode, který vyžaduje editor XML sady Visual Studio.

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Zkopírování souboru definice schématu z tématu nápovědy

1. Vyhledejte téma nápovědy obsahující definici schématu, jak je popsáno dříve v tomto tématu.

    - Pro soubory. dbml si přečtěte téma [generování kódu v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - Pro externí soubory mapování viz [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

2. Kliknutím na **Kopírovat kód** zkopírujte soubor kódu do schránky.

3. Spusťte Poznámkový blok pro vytvoření nového souboru.

4. Vložte kód ze schránky do souboru poznámkového bloku.

5. V nabídce **soubor** poznámkového bloku klikněte na **Uložit jako**.

6. V poli **kódování** vyberte **Unicode**.

    > [!IMPORTANT]
    > Tento výběr zaručuje, že značka`FFFE`pořadí bajtů v kódování Unicode-16 je do textového souboru předpona.

7. V poli **název souboru** vytvořte název souboru s příponou. xsd.

## <a name="see-also"></a>Viz také:

- [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
