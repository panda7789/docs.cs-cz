---
title: 'Postupy: Ověření DBML a externí soubory mapování'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 42cba5b9b686f5f94d4ebf8f889461e1bab009b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692727"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Postupy: Ověření DBML a externí soubory mapování
Externí soubory mapování a dbml soubory, které můžete upravit musí být ověřena jejich odpovídajících schématu definice. Toto téma poskytuje uživatelům aplikace Visual Studio s kroky k implementaci procesu ověřování.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>K ověření dbml nebo soubor XML  
  
1.  V sadě Visual Studio **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **souboru**.  
  
2.  V **otevřít soubor** dialogového okna klikněte na dbml nebo soubor mapování XML, který chcete ověřit.  
  
     Soubor se otevře v **editoru XML**.  
  
3.  Klikněte pravým tlačítkem myši okno a potom klikněte na tlačítko **vlastnosti**.  
  
4.  V **vlastnosti** okna, klikněte na tlačítko se třemi tečkami pro **schémata** vlastnost.  
  
     **Schémat XML** zobrazí se dialogové okno.  
  
5.  Mějte na paměti příslušného schématu definice pro požadovaný účel.  
  
    -   DbmlSchema.xsd je definice schématu pro ověření souboru .dbml. Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd je definice schématu pro ověřování externí soubor mapování XML. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  V **použití** sloupec řádku definice požadované schéma, otevřete rozevírací seznam a potom klepněte na tlačítko **použít tohle schéma**.  
  
     Definiční soubor schématu je teď přidružené k vaší DBML nebo XML souboru mapování.  
  
     Zkontrolujte, zda že jsou vybrány žádné definice schémat.  
  
7.  Na **zobrazení** nabídky, klikněte na tlačítko **seznam chyb**.  
  
     Určení, zda byly vytvořeny chyby, varování nebo zprávy. V opačném případě je soubor XML platný pro definici schématu.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Alternativní metoda pro poskytnutí definice schématu  
 Pokud z nějakého důvodu odpovídající XSD souborů se nezobrazují v **schémat XML** dialogovém okně soubor XSD si můžete stáhnout z tématu nápovědy. Následující kroky vám pomůžou ušetřit stažený soubor ve formátu Unicode, vyžaduje pomocí editoru XML sady Visual Studio.  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Zkopírujte soubor definice schématu z tématu nápovědy  
  
1.  Téma nápovědy, který obsahuje definici schématu, jak je popsáno výše v tomto tématu.  
  
    -   Soubory dbml, naleznete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Externí soubory mapování, naleznete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Klikněte na tlačítko **kopírování kódu** do souboru s kódem zkopírujte do schránky.  
  
3.  Spusťte Poznámkový blok a vytvořte nový soubor.  
  
4.  Vložte kód ze schránky do soubor poznámkového bloku.  
  
5.  Na poznámkového bloku **souboru** nabídky, klikněte na tlačítko **uložit jako**.  
  
6.  V **kódování** vyberte **Unicode**.  
  
    > [!IMPORTANT]
    >  Tento výběr zaručuje, že značky pořadí bajtů kódování Unicode-16 (`FFFE`) se přidá jako předpona do textového souboru.  
  
7.  V **název_souboru** pole, vytvořte soubor s příponou XSD.  
  
## <a name="see-also"></a>Viz také:
- [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
