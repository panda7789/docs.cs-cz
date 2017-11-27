---
title: "Přidávání tiskových sestav do aplikací v jazyce Visual Studio"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ce2a8b12d8202a9f201a82b0d4a571249210d48
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Přidávání tiskových sestav do aplikací v jazyce Visual Studio
Visual Studio podporuje celou řadu řešení pro sestavy můžete přidat bohaté data sestavy do aplikace Visual Basic. Můžete vytvořit a přidat sestav pomocí ovládacích prvků prohlížeče sestav, Crystal Reports nebo SQL Server Reporting Services.  
  
> [!NOTE]
>  SQL Server Reporting Services je součástí systému SQL Server 2005, nikoli Visual Studio. Služba Reporting Services není nainstalován v počítači, pokud jste nainstalovali systém SQL Server 2005.  
  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Přehled služby Microsoft Reporting technologie v aplikacích jazyka Visual Basic  
 Vyberte z následujících dvou přístupů pomocí služby Microsoft reporting technologii ve vaší aplikaci:  
  
-   Přidejte jednu nebo více instancí ovládacího prvku prohlížeče sestav do aplikace Windows Visual Basic.  
  
-   Integrace prostřednictvím kódu programu SQL Server Reporting Services tak, že volání webové službě Server sestav.  
  
-   Pomocí ovládacího prvku prohlížeče sestav a Microsoft SQL Server 2005 Reporting Services společně pomocí ovládacího prvku jako prohlížeč sestav a server sestav jako procesoru. (Všimněte si, SQL Server 2005 verzí služby Reporting Services musíte použít, pokud chcete použít server sestav a ovládací prvek prohlížeče sestav společně).  
  
## <a name="using-reportviewer-controls"></a>Použití ovládacích prvků prohlížeče sestav  
 Přidání ovládacího prvku prohlížeče sestav do formuláře v aplikaci je nejjednodušší způsob, jak funkce sestavy do aplikace Windows Visual Basic pro vložení. Ovládací prvek přidá sestavy zpracování možnosti přímo do vaší aplikace a obsahuje integrovaný návrhář sestav tak, že můžete vytvořit sestavy pomocí dat z libovolného objektu dat ADO.NET. Rozhraní API plné zajišťují programový přístup k ovládacímu prvku a sestavy tak, aby můžete nakonfigurovat spuštění funkce.  
  
 Prohlížeče sestav poskytuje předdefinované sestavy zpracování a možnost zobrazení v ovládacím prvku jeden, volně distribuovatelného data. Zvolte ReportViewer pokud vyžadujete funkci následující sestavy:  
  
-   Zpracování v aplikaci klienta sestav. Zpracované sestavy se zobrazí v oblasti zobrazení poskytované ovládacího prvku.  
  
-   Datová vazba na tabulky dat ADO.NET. Můžete vytvořit sestavy, které využívají <xref:System.Data.DataTable> instance zadaný do ovládacího prvku. Můžete také navázat přímo na obchodní objekty.  
  
-   Distribuovatelné ovládací prvky, které můžete zahrnout do vaší aplikace.  
  
-   Funkcionalita modulu runtime například navigaci na stránce, tisk, vyhledávání a export formátů. Panelu nástrojů prohlížeče sestav poskytuje podporu pro tyto operace.  
  
 Použití ovládacího prvku prohlížeče sestav, můžete přetáhnout z **Data** části nástrojů Visual Studio do formuláře v aplikaci Windows Visual Basic.  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>Vytváření sestav v sadě Visual Studio pro ovládací prvky prohlížeče sestav  
 Chcete-li vytvořit sestavu, která běží v prohlížeče sestav, přidejte **sestavy** šablony do projektu. Visual Studio vytvoří soubor definice sestav (.rdlc) klienta, přidá soubor do projektu a otevře integrovaný návrhář sestav v pracovním prostoru Visual Studio.  
  
 Návrhář sestav Visual Studio se integruje s **zdroje dat** okno. Když přetáhněte pole ze **zdroje dat** časové období pro sestavu, Návrhář sestav zkopíruje metadata o zdroji dat do souboru definice sestavy. Tato metadata pomocí ovládacího prvku prohlížeče sestav slouží k automatickému generování kódu datové vazby.  
  
 Návrhář sestav Visual Studio neobsahuje funkce Náhled sestavy. Zobrazit náhled sestavy, spusťte aplikaci a náhled sestavy jej.  
  
|Chcete-li přidat funkce základní sestavy do vaší aplikace|  
|---|    
|1.  Přetáhněte ovládací prvek prohlížeče sestav z **Data** kartě **sada nástrojů** do formuláře.<br />2.  Na **projektu** nabídce zvolte **přidat novou položku**. V **přidat novou položku** dialogové okno, vyberte **sestavy** ikonu a klikněte na tlačítko **přidat**.<br />     Návrhář sestav se otevře ve vývojovém prostředí, a soubor sestav (.rdlc) je přidán do projektu.<br />3.  Přetáhněte položky sestavy z **sada nástrojů** na rozložení sestavy a seřadit je podle potřeby.<br />4.  Přetáhněte pole ze **zdroje dat** okno na položky sestavy v rozložení sestavy.|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Použití služby Reporting Services v aplikacích jazyka Visual Basic  
 Na serveru vytváření sestav technologie, která je součástí systému SQL Server Reporting Services je. Služba Reporting Services zahrnuje další funkce, které nejsou k dispozici v ovládací prvky prohlížeče sestav. Vyberte služby Reporting Services, pokud budete potřebovat některé z následujících funkcí:  
  
-   Nasazení s více instancemi a zpracování serveru sestav, který poskytuje lepší výkon pro komplexní nebo dlouhotrvající sestavy a pro sestavy vysoký počet aktivit.  
  
-   Integrované dat a zpracování sestavy, se podpora pro ovládací prvky vlastních sestav a bohaté vykreslování výstupní formáty.  
  
-   Naplánovat, zpracování sestav tak, aby můžete zadat přesně dobu spuštění sestavy.  
  
-   Distribuce sestav prostřednictvím e-mailu nebo do umístění sdílené složky souborů.  
  
-   Vykazování ad hoc tak, aby obchodní uživatelé můžete vytvořit sestavy, podle potřeby.  
  
-   Řízené daty předplatná, která se bude směrovat výstup vlastních sestav dynamické seznam příjemců.  
  
-   Vlastní rozšíření pro zpracování dat, doručení sestavy, vlastní ověřování a vykreslování sestavy.  
  
 Server sestav je implementovaný jako webovou službu. Kód aplikace musí obsahovat volání webové služby pro přístup k sestavám a další metadata. Webová služba poskytuje úplný programový přístup k instanci serveru sestav.  
  
 Vzhledem k tomu, že služby Reporting Services je technologie vytváření sestav založené na webu, výchozí prohlížeč zobrazí sestavy, které jsou generovány ve formátu HTML. Pokud nechcete použít HTML jako výchozí formát prezentace sestav, budete muset napsat vlastní prohlížeč sestav pro vaši aplikaci.  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Vytváření sestav v sadě Visual Studio pro služby vytváření sestav  
 Pro vytváření sestav, které běží na serveru sestav, vytváření definice sestavy (.rdl) souborů v sadě Visual Studio prostřednictvím Business Intelligence Development Studio, který je součástí systému SQL Server 2005.  
  
> [!NOTE]
>  Musí mít systém SQL Server 2005, aby bylo možné používat SQL Server Reporting Services a Business Intelligence Development Studio.  
  
 Business Intelligence Development Studio. Přidá šablony projektů, které jsou specifické pro součásti systému SQL Server. K vytváření sestav, můžete z **projektu serveru sestav** nebo **Průvodce projektem Report Server** šablony. Můžete zadat připojení ke zdroji dat a dotazy na celou řadu typy zdrojů dat, včetně systému SQL Server, Oracle, služby Analysis Services, XML a SQL Server Integration Services. A **Data** kartě **rozložení** kartě a **Preview** kartě umožňují definovat data, vytvářet rozložení sestavy a prohlédnout sestava všechno ve stejném pracovním prostoru.  
  
 Definice sestavy, které vytvoříte pro ovládací prvek nebo server sestav lze znovu použít v obou technologií.  
  
|Chcete-li vytvořit sestavu, která běží na serveru sestav|  
|---|    
|1.  Na **soubor** nabídce zvolte **nový**.<br />     **Nový projekt** otevře se dialogové okno.<br />2.  V **typy projektů** podokně klikněte na tlačítko **projekty Business Intelligence**.<br />3.  V podokně šablon vyberte **projektu serveru sestav** nebo **Průvodce projektem Report Server**.|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>Pomocí ovládacích prvků prohlížeče sestav a SQL Server Reporting Services  
 Ovládací prvky prohlížeče sestav a SQL Server 2005 Reporting Services můžete použít společně ve stejné aplikaci.  
  
-   Ovládací prvek prohlížeče sestav poskytuje prohlížeč, který se používá k zobrazení sestavy v aplikaci.  
  
-   Služba Reporting Services poskytuje sestavy a provádí veškeré zpracování na vzdáleném serveru.  
  
 Ovládací prvek prohlížeče sestav lze nakonfigurovat k zobrazení sestavy, které jsou uloženy a zpracovány na vzdálený server sestav služby Reporting Services. Tento typ konfigurace se nazývá *režim vzdálené zpracování*. Ovládací prvek v režimu vzdálené zpracování požadavků sestavu, která je uložena na serveru vzdáleného sestav. Server sestav provádí zpracování sestavy, zpracování dat a vykreslování sestavy. Dokončené, sestavené sestavy se vrátí do ovládacího prvku a zobrazí v oblasti zobrazení.  
  
 Sestavy, které běží na serveru sestav další podporu exportovat formátů, jinou parametrizaci sestava, použijte typy zdrojů dat, které jsou podporovány serverem sestav a jsou přístupné prostřednictvím modelu autorizace na základě rolí na server sestav.  
  
 Pro použití režimu vzdálené zpracování, zadejte adresu URL a cestu k serveru sestav při konfiguraci ovládacího prvku prohlížeče sestav.
