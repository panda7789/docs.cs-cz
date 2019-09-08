---
title: Učení podle návodů
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: 4beb9944a13fd2f76d7305b4d84230fcc33483be
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781313"
---
# <a name="learning-by-walkthroughs"></a>Učení podle návodů
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dokumentace nabízí několik návodů. Toto téma řeší některé obecné postupy (včetně řešení potíží) a poskytuje odkazy na několik podrobných návodů ke vstupní úrovni pro získání [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]informací o nástroji.  
  
> [!NOTE]
> Návody v tomto Začínáme části ukazují na základní kód, který podporuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii. V praxi obvykle použijete projekty Návrhář relací objektů a model Windows Forms k implementaci vašich [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikací. Dokumentace k Návrháři O/R poskytuje příklady a návody pro tento účel.  
  
## <a name="getting-started-walkthroughs"></a>Začínáme návody  
 V této části jsou k dispozici několik návodů. Tyto návody jsou založené na ukázkové databázi Northwind a prezentují [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkce za mírného tempa s minimálními složitými složitostmi.  
  
 Typický postup, jak postupovat, je následující:  
  
|Cíle|Visual Basic|C#|  
|---------------|------------------|---------|  
|Vytvořte třídu entity a spusťte jednoduchý dotaz.|[Návod: Jednoduchý objektový model a dotaz (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md)|[Návod: Jednoduchý objektový model a dotaz (C#)](walkthrough-simple-object-model-and-query-csharp.md)|  
|Přidejte druhou třídu a spusťte složitější dotaz.<br /><br /> (Vyžaduje dokončení předchozího návodu).|[Návod: Dotazování napříč relacemi (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md)|[Návod: Dotazování napříč relacemiC#()](walkthrough-querying-across-relationships-csharp.md)|  
|Přidávat, měnit a odstraňovat položky v databázi.|[Návod: Manipulace s daty (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)|[Návod: Manipulace s daty (C#)](walkthrough-manipulating-data-csharp.md)|  
|Použijte uložené procedury.|[Návod: Použití pouze uložených procedur (Visual Basic)](walkthrough-using-only-stored-procedures-visual-basic.md)|[Návod: Použití pouze uložených procedur (C#)](walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Obecné  
 Následující informace, které se týkají těchto návodů, jsou obecně:  
  
- Hlediska Každý [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] návod používá Visual Studio jako integrované vývojové prostředí (IDE).  
  
- Moduly SQL: Tyto návody jsou zapsány k implementaci pomocí SQL Server Express. Pokud nemáte SQL Server Express, můžete si ho zdarma stáhnout. Další informace najdete v tématu [stažení ukázkových databází](downloading-sample-databases.md).  
  
    > [!NOTE]
    > [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Návody používají název souboru jako připojovací řetězec. Pouhým zadáním názvu souboru je to pohodlí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , které poskytuje SQL Server Express uživatelům. Vždycky věnujte pozornost problémům se zabezpečením. Další informace najdete v tématu [zabezpečení v LINQ to SQL](security-in-linq-to-sql.md).  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Návody obvykle vyžadují ukázkovou databázi Northwind. Další informace najdete v tématu [stažení ukázkových databází](downloading-sample-databases.md).  
  
- Dialogová okna a příkazy nabídek, které vidíte v návodech, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici sady Visual Studio. Chcete-li změnit nastavení, klikněte na položku **Nastavení importu a exportu** v nabídce **nástroje** . Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
- Pro návody, které řeší scénáře s více vrstvami, musí být server umístěn v počítači, který se liší od vývojového počítače, a musíte mít příslušná oprávnění pro přístup k serveru.  
  
- Název třídy, která obvykle představuje tabulku Orders v ukázkové databázi `[Order]`Northwind. Uvozovací znaky jsou vyžadovány, `Order` protože je klíčové slovo v Visual Basic.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 K běhovým chybám může dojít, protože nemáte dostatečná oprávnění pro přístup k databázím používaným v těchto návodech. Pomocí následujících kroků můžete vyřešit nejběžnější tyto problémy.  
  
### <a name="log-on-issues"></a>Problémy s přihlášením  
 Vaše aplikace se může pokusit o přístup k databázi prostřednictvím přihlášení k databázi, které nepřijímá.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Ověření nebo změna protokolu databáze na  
  
1. V nabídce **Start** systému Windows přejděte na **všechny programy**, **Microsoft SQL Server 2005**, přejděte na **konfigurační nástroje**a pak klikněte na **SQL Server Configuration Manager**.  
  
2. V levém podokně **Configuration Manager SQL Server**klikněte na **SQL Server 2005 služby**.  
  
3. V pravém podokně klikněte pravým tlačítkem na **SQL Server (SQLEXPRESS)** a pak klikněte na **vlastnosti**.  
  
4. Klikněte na kartu **přihlášení** a ověřte, jak se snažíte přihlásit k serveru.  
  
     Ve většině případů funguje **místní systém** .  
  
     Pokud provedete změnu, restartujte službu kliknutím na tlačítko **restartovat** .  
  
### <a name="protocols"></a>Protokolů  
 V některých případech se nemusí správně nastavit protokoly, aby vaše aplikace měla přístup k databázi. Například protokol **pojmenovaných kanálů** , který je požadován pro návody v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], není ve výchozím nastavení povolen.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Povolení protokolu pojmenovaných kanálů  
  
1. V levém podokně **SQL Server Configuration Manager**rozbalte položku **konfigurace sítě SQL Server 2005**a potom klikněte na **protokoly pro SQLEXPRESS**.  
  
2. V pravém podokně se ujistěte, že je povolen protokol **pojmenovaných kanálů** . Pokud ne, klikněte pravým tlačítkem myši na položku **Názvové kanály** a potom klikněte na možnost **Povolit**.  
  
     Budete muset službu zastavit a restartovat. Postupujte podle kroků v následujícím bloku.  
  
### <a name="stopping-and-restarting-the-service"></a>Zastavení a restartování služby  
 Aby se změny projevily, musíte zastavit a restartovat služby.  
  
##### <a name="to-stop-and-restart-the-service"></a>Zastavení a restartování služby  
  
1. V levém podokně **Configuration Manager SQL Server**klikněte na **SQL Server 2005 služby**.  
  
2. V pravém podokně klikněte pravým tlačítkem na **SQL Server (SQLEXPRESS)** a pak klikněte na **zastavit**.  
  
3. Pravým tlačítkem myši klikněte na **SQL Server (SQLEXPRESS)** a pak klikněte na **restartovat**.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](getting-started.md)
