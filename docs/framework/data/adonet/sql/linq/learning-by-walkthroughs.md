---
title: "Učení dle návody"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38961451a51ae47d05d7625ee0e83da97261eb0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="learning-by-walkthroughs"></a>Učení dle návody
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dokumentace poskytuje několik návody. Toto téma řeší problémy některé obecné návod (včetně řešení potíží) a poskytuje odkazy na několik vstupní úrovně návody pro získání informací o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Názorné postupy v této části Začínáme umístěte je do základní kód, který podporuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie. V praxi, obvykle použijete [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] a projekty Windows Forms k implementaci vašeho [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Dokumentace obsahuje příklady a návody pro tento účel.  
  
## <a name="getting-started-walkthroughs"></a>Začínáme návody  
 V této části jsou k dispozici několik návody. Tyto postupy jsou založené na vzorovou databázi Northwind a prezentovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkce jemného tempem s minimálním složité kroky.  
  
 Typický průběh podle vypadat takto:  
  
|Cíl|Visual Basic|C#|  
|---------------|------------------|---------|  
|Vytvořte třídu entity a provést jednoduchý dotaz.|[Návod: Jednoduché objektový Model a dotazů (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[Návod: Jednoduché objektový Model a dotazů (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|Přidání třídy sekundu a provedení složitější dotazu.<br /><br /> (Vyžaduje dokončení předchozího návodu).|[Návod: Dotazování napříč relacemi (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[Návod: Dotazování napříč relacemi (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|Přidat, měnit a odstraňovat položky v databázi.|[Návod: Manipulace s daty (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[Návod: Manipulace s daty (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|Pomocí uložených procedur.|[Návod: Použití pouze uložené procedury (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[Návod: Použití pouze uložené procedury (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Obecné  
 Tyto informace se vztahují na tyto návody obecně:  
  
-   Prostředí: Každý [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] návod používá [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] jako jeho integrované vývojové prostředí (IDE).  
  
-   Moduly SQL: tyto postupy jsou zapsány k implementaci pomocí SQL Server Express. Pokud nemáte, SQL Server Express, můžete stáhnout zdarma. Další informace najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]návody použít název souboru jako připojovací řetězec. Stačí zadat název souboru je pro vaše pohodlí, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro uživatele, systém SQL Server Express. Vždy věnujte pozornost problémy se zabezpečením. Další informace najdete v tématu [zabezpečení v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]návody obvykle vyžadují ukázková databáze Northwind. Další informace najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
-   Dialogová okna a příkazy nabídky můžete vidět v návody se může lišit od těch popsaných v nápovědě, v závislosti na nastavení active nebo [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] edition. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
-   Pro návody, které řeší scénáře s několika vrstvami server musí být umístěn v počítači, který se liší od vývojovém počítači a musí mít příslušná oprávnění pro přístup k serveru.  
  
-   Název třídy, která obvykle představuje objednávky tabulky v ukázkové databázi Northwind je `[Order]`. Uvození není nutná, protože `Order` je klíčové slovo v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)].  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Běhové chyby může dojít, protože nemáte dostatečná oprávnění pro přístup k databázím použít v těchto kurzů. Viz následující postup nejběžnější tyto problémy vyřešit.  
  
### <a name="log-on-issues"></a>Problémy přihlášení  
 Aplikace může být pokusu o přístup k databázi prostřednictvím přihlášení k databázi, které nepřijímá.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Ověřte nebo změňte databázi přihlášení  
  
1.  V systému Windows **spustit** nabídky, přejděte na příkaz **všechny programy**, **Microsoft SQL Server 2005**, přejděte na příkaz **nástroje pro konfiguraci**a potom klikněte na **Správce konfigurace systému SQL Server**.  
  
2.  V levém podokně **SQL Server Configuration Manager**, klikněte na tlačítko **služeb SQL Server 2005**.  
  
3.  V pravém podokně klikněte pravým tlačítkem na **SQL Server (SQLEXPRESS)**a potom klikněte na **vlastnosti**.  
  
4.  Klikněte **přihlášení** kartě a ověřte, jak se pokoušíte přihlásit k serveru.  
  
     Ve většině případů **místní systém** funguje.  
  
     Pokud provedete změny, klikněte na tlačítko **restartujte** restartování služby.  
  
### <a name="protocols"></a>protokoly  
 V některých případech nemusí protokoly nastavit správně pro vaši aplikaci pro přístup k databázi. Například **pojmenovaných kanálů** protokol, který je vyžadován pro názorné postupy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], není ve výchozím nastavení povolené.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Chcete-li povolit protokol pojmenovaných kanálů  
  
1.  V levém podokně **SQL Server Configuration Manager**, rozbalte položku **konfigurace sítě serveru SQL Server 2005**a potom klikněte na **protokoly pro funkci SQLEXPRESS**.  
  
2.  V pravém podokně, ujistěte se, že **pojmenovaných kanálů** je povolen protokol. Pokud není, klikněte pravým tlačítkem na **název kanály** a pak klikněte na **povolit**.  
  
     Je nutné zastavit a restartovat službu. Postupujte podle kroků v další blok.  
  
### <a name="stopping-and-restarting-the-service"></a>Zastavení a restartování služby  
 Můžete zastavit a restartovat služby, než změny se projeví.  
  
##### <a name="to-stop-and-restart-the-service"></a>Chcete-li zastavit a restartovat službu  
  
1.  V levém podokně **SQL Server Configuration Manager**, klikněte na tlačítko **služeb SQL Server 2005**.  
  
2.  V pravém podokně klikněte pravým tlačítkem na **SQL Server (SQLEXPRESS)**a potom klikněte na **Zastavit**.  
  
3.  Klikněte pravým tlačítkem na **SQL Server (SQLEXPRESS)**a potom klikněte na **restartujte**.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
