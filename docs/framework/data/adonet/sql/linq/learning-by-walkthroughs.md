---
title: Učení podle návodů
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: 1386d0e8fadddab5cd15818cb616bf331262e654
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872488"
---
# <a name="learning-by-walkthroughs"></a>Učení podle návodů
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dokumentace poskytuje několik návody. Toto téma řeší některé problémy obecného průvodce (včetně Poradce při potížích) a obsahuje odkazy na několik základní návody pro získání informací o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Názorné postupy v této části Začínáme se službou můžete zpřístupnit základního kódu, který podporuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie. V praxi, budete obvykle používat [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] projekty Windows Forms k implementaci a vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikací. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Dokumentace poskytuje příklady a názorné postupy pro tento účel.  
  
## <a name="getting-started-walkthroughs"></a>Začínáme se službou názorné postupy  
 V této části jsou k dispozici několik návody. Tyto kurzy vycházejí z ukázkové databáze Northwind a prezentovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkce mírného tempem s minimálními složitosti.  
  
 Typický průběh sledovat by měl vypadat takto:  
  
|Cíl|Visual Basic|C#|  
|---------------|------------------|---------|  
|Vytvořte třídu entity a provedení jednoduchého dotazu.|[Návod: Jednoduchý objektový model a dotaz (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[Návod: Jednoduchý objektový model a dotaz (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|Přidejte druhé třídu a provedení složitějšího dotazu.<br /><br /> (Vyžaduje dokončení předchozím návodu).|[Návod: Dotazování napříč relacemi (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[Návod: Dotazování napříč relacemi (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|Přidat, změnit a odstraňovat položky v databázi.|[Návod: Manipulace s daty (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[Návod: Manipulace s daty](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|Použití uložených procedur.|[Návod: Použití jen uložených procedur (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[Návod: Použití jen uložených procedur (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Obecné  
 Tyto informace se vztahují na tyto kurzy obecně platí:  
  
-   Prostředí: Každý [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] návod používá jako jeho integrované vývojové prostředí (IDE) sady Visual Studio.  
  
-   Moduly SQL: tyto postupy jsou zapsány do implementovaná pomocí systému SQL Server Express. Pokud nemáte SQL Server Express, můžete stáhnout zdarma. Další informace najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] návody pro použití názvu souboru jako připojovací řetězec. Stačí zadat název souboru je usnadnění, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro uživatele systému SQL Server Express. Vždy věnujte pozornost problémy se zabezpečením. Další informace najdete v tématu [zabezpečení v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] návody pro obvykle vyžadují ukázkové databáze Northwind. Další informace najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
-   Dialogová okna a příkazy nabídek, které se zobrazí v návodech může lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici Visual Studio. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
-   Návody, které odkazují na víceúrovňové scénáře server se musí nacházet v počítači, který se liší od vývojového počítače a musí mít příslušná oprávnění pro přístup k serveru.  
  
-   Je název třídy, která obvykle představuje v tabulce objednávky v ukázkové databázi Northwind `[Order]`. Uvození se totiž `Order` je klíčové slovo v jazyce Visual Basic.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Protože nemáte dostatečná oprávnění pro přístup k databází používaných v těchto kurzech, může dojít k chybám za běhu. Viz následující postup vám pomůže vyřešit nejčastější z těchto problémů.  
  
### <a name="log-on-issues"></a>Problémy s přihlášení  
 Pro přístup k databázi pomocí přihlášení k databázi, které nepřijímá asi zkouší vaší aplikace.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Ověřit nebo změnit databázi přihlášení  
  
1.  V Windows **Start** nabídky, přejděte k **všechny programy**, **Microsoft SQL Server 2005**, přejděte na **konfigurační nástroje**a potom klikněte na **Správce konfigurace systému SQL Server**.  
  
2.  V levém podokně **Správce konfigurace systému SQL Server**, klikněte na tlačítko **služeb SQL Server 2005**.  
  
3.  V pravém podokně klikněte pravým tlačítkem na **SQL serveru (SQLEXPRESS)** a potom klikněte na tlačítko **vlastnosti**.  
  
4.  Klikněte na tlačítko **přihlášení** kartě a ověřte, jak se pokoušíte přihlásit k serveru.  
  
     Ve většině případů **místní systém** funguje.  
  
     Pokud provedete změny, klikněte na tlačítko **restartovat** restartování služby.  
  
### <a name="protocols"></a>Protokoly  
 V některých případech nemusí protokoly nastavit správně pro vaši aplikaci pro přístup k databázi. Například **pojmenovaných kanálů** protokolu, která je potřebná pro návody v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], není ve výchozím nastavení povolená.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Chcete-li povolit protokol pojmenovaných kanálů  
  
1.  V levém podokně **Správce konfigurace systému SQL Server**, rozbalte **síťová konfigurace systému SQL Server 2005**a potom klikněte na tlačítko **protokoly pro SQLEXPRESS**.  
  
2.  V pravém podokně, ujistěte se, že **pojmenovaných kanálů** je povolený protokol. Pokud není, klikněte pravým tlačítkem na **pojmenované kanály** a potom klikněte na tlačítko **povolit**.  
  
     Budete muset zastavit a restartovat službu. Postupujte podle kroků v další blok.  
  
### <a name="stopping-and-restarting-the-service"></a>Zastavení a restartování služby  
 Musíte zastavit a znovu spustit služby předtím, než se změny projeví.  
  
##### <a name="to-stop-and-restart-the-service"></a>Zastavit a restartovat službu  
  
1.  V levém podokně **Správce konfigurace systému SQL Server**, klikněte na tlačítko **služeb SQL Server 2005**.  
  
2.  V pravém podokně klikněte pravým tlačítkem na **SQL serveru (SQLEXPRESS)** a potom klikněte na tlačítko **Zastavit**.  
  
3.  Klikněte pravým tlačítkem na **SQL serveru (SQLEXPRESS)** a potom klikněte na tlačítko **restartovat**.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
