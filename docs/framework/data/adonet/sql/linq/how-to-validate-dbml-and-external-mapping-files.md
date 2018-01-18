---
title: "Postupy: ověření DBML a externí mapování souborů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7724586c33c19654c3657a5a4604a3c74f2c8756
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Postupy: ověření DBML a externí mapování souborů
Externí mapování soubory a soubory dbml, které můžete upravit, musí být ověřený proti jejich definice příslušného schématu. Toto téma obsahuje [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] uživatelům s kroky pro implementaci procesu ověření.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>K ověření souboru XML nebo dbml  
  
1.  V sadě Visual Studio **soubor** nabídky, přejděte na příkaz **otevřete**a potom klikněte na **soubor**.  
  
2.  V **otevření souboru** dialogové okno pole, klikněte na dbml nebo mapování souboru XML, který chcete ověřit.  
  
     Soubor se otevře v **editoru XML**.  
  
3.  Klikněte pravým tlačítkem na okna a pak klikněte na **vlastnosti**.  
  
4.  V **vlastnosti** okně klikněte na tlačítko se třemi tečkami pro **schémata** vlastnost.  
  
     **Schémat XML** otevře se dialogové okno.  
  
5.  Všimněte si definici příslušného schématu pro požadovaný účel.  
  
    -   DbmlSchema.xsd je definice schématu pro ověření souboru DBML. Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd je definice schématu pro ověření externí mapování souboru XML. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  V **použití** sloupec požadované schéma definice řádku, klikněte na tlačítko Otevřít rozevíracího seznamu a pak klikněte na tlačítko **toto schéma používají**.  
  
     Soubor definice schématu je teď přidružené k vaší DBML nebo mapování souboru XML.  
  
     Zkontrolujte, zda že jsou vybrány žádné definice schémat.  
  
7.  Na **zobrazení** nabídky, klikněte na tlačítko **seznam chyb**.  
  
     Určí, zda byly vygenerovány chyby, upozornění nebo zprávy. Pokud ne, je soubor XML platný proti definici schématu.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Alternativní metoda pro zadávání definice schématu  
 Pokud z nějakého důvodu odpovídající XSD souboru není uveden v **schémat XML** dialogové okno, soubor XSD můžete stáhnout z tématu nápovědy. Následující kroky nápovědy uložte stažený soubor ve formátu Unicode vyžaduje [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] editoru XML.  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Zkopírujte soubor definice schématu z tématu nápovědy  
  
1.  Najděte téma nápovědy, který obsahuje definici schématu, jak je popsáno výše v tomto tématu.  
  
    -   Soubory dbml, najdete v části [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Externí mapování soubory, najdete v části [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Klikněte na tlačítko **kopie kódu** při kopírování souboru kódu do schránky.  
  
3.  Spusťte program Poznámkový blok k vytvoření nového souboru.  
  
4.  Vložte kód ze schránky do souboru poznámkového bloku.  
  
5.  Na Poznámkový blok **soubor** nabídky, klikněte na tlačítko **uložit jako**.  
  
6.  V **kódování** vyberte **Unicode**.  
  
    > [!IMPORTANT]
    >  Tento výběr zaručuje, že značky pořadí bajtů kódování Unicode-16 (`FFFE`) se přidá jako předpona do textového souboru.  
  
7.  V **název souboru** pole, vytvořte název souboru s příponou XSD.  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
