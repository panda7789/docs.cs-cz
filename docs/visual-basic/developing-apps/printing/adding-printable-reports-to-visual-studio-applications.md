---
title: Přidávání tiskových sestav do aplikací v jazyce Visual Studio
ms.date: 07/20/2015
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
ms.openlocfilehash: 65264deea3aeff1a633ea6888b3f175031b7fba5
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212011"
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Přidávání tiskových sestav do aplikací v jazyce Visual Studio
Visual Studio podporuje širokou škálu řešení pro sestavy k přidání bohatého vykazování dat do aplikace Visual Basic. Můžete vytvořit a přidat sestavy, které používají ovládací prvky prohlížeče sestav, Crystal Reports nebo SQL Server Reporting Services.  

  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Přehled služby Microsoft Reporting technologie v aplikacích jazyka Visual Basic  
 Zvolte z následujících postupů použít služby Microsoft reporting technologií ve vaší aplikaci:  
  
-   Přidejte jednu nebo víc instancí ovládacího prvku prohlížeče sestav do aplikací Windows v jazyce Visual Basic.  
  
-   Integrace služby SQL Server Reporting Services prostřednictvím kódu programu tím, že volání webovou službu Server sestav.  
  
-   Pomocí ovládacího prvku prohlížeče sestav a Microsoft SQL Server 2005 Reporting Services společně, pomocí ovládacího prvku prohlížeče sestav a server sestav jako zpracovatele sestavy. (Mějte na paměti, pokud chcete používat server sestav a ovládací prvek prohlížeče sestav společně musí používat verzi SQL Server 2005 Reporting Services).  
  
## <a name="using-reportviewer-controls"></a>Použití ovládacích prvků prohlížeče sestav  
 Přidání ovládacího prvku ReportViewer na formulář v nástrojích pro vaše aplikace je nejjednodušší způsob, jak vložení funkce sestavy do aplikace Windows v jazyce Visual Basic. Ovládací prvek přidá zprávu zpracování funkcí přímo do vaší aplikace a poskytuje integrovaný návrhář sestav, takže můžete vytvářet sestavy pomocí dat z libovolného objektu dat ADO.NET. Plně funkční rozhraní API poskytuje programový přístup k ovládacím prvku a sestavy tak, abyste mohli nakonfigurovat funkce za běhu.  
  
 Prohlížeče sestav poskytuje zpracování předdefinované sestavy a možnost zobrazení v jediné, volně Distribuovatelný ovládacího prvku. Zvolte, pokud budete potřebovat následující sestavy funkce ovládací prvky prohlížeče sestav:  
  
-   Zpracování v klientské aplikaci sestavy. Zpracované sestavy se zobrazí v oblasti zobrazení poskytuje ovládací prvek.  
  
-   Vazba dat na tabulky dat ADO.NET. Můžete vytvořit sestavy, které využívají <xref:System.Data.DataTable> instance zadat do ovládacího prvku. Můžete také navázat přímo na obchodní objekty.  
  
-   Distribuovatelné ovládací prvky, které můžete zahrnout do vaší aplikace.  
  
-   Funkcionalita modulu runtime, jako je například navigace po stránkách, tisk, vyhledávání a export formáty. Panelu nástrojů prohlížeče sestav poskytuje podporu pro tyto operace.  
  
 Použití ovládacího prvku ReportViewer, ji můžete přetáhnout z **Data** části Visual Studio Toolbox na formulář v nástrojích pro aplikace Windows v jazyce Visual Basic.  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>Vytváření sestav v sadě Visual Studio pro ovládací prvky prohlížeče sestav  
 Chcete-li vytvořit sestavu, která běží v prohlížeče sestav, přidejte **sestavy** šablonu do vašeho projektu. Visual Studio vytvoří soubor definice sestav klienta (.rdlc), přidá soubor do projektu a integrovaný návrhář sestav se otevře v pracovním prostoru aplikace Visual Studio.  
  
 Návrhář sestav pro Visual Studio se integruje s **zdroje dat** okna. Při přetažení pole z **zdroje dat** okna sestavy, v Návrháři sestav zkopíruje metadata o zdroji dat do souboru definice sestavy. Tato metadata používá k automatickému generování kódu datové vazby ovládacího prvku ReportViewer.  
  
 Návrhář sestav pro Visual Studio neobsahuje funkci Náhled sestavy. Zobrazit náhled sestavy, spusťte aplikaci a zobrazit jejich náhled sestavy vložené v ní.  
  
|Chcete-li přidat funkce základní sestavy do vaší aplikace|  
|---|    
|1.  Přetáhněte ovládací prvek prohlížeče sestav z **Data** karty **nástrojů** do formuláře.<br />2.  Na **projektu** nabídce zvolte **přidat novou položku**. V **přidat novou položku** dialogové okno, vyberte **sestavy** ikonu a klikněte na tlačítko **přidat**.<br />     Ve vývojovém prostředí se otevře v Návrháři sestav a souborů sestav (.rdlc) se přidá do projektu.<br />3.  Přetáhněte položky sestavy z **nástrojů** na rozložení sestavy a uspořádat je, jak chcete.<br />4.  Přetáhnout pole ze **zdroje dat** okno na položky sestavy v rozložení sestavy.|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Použití služby Reporting Services v aplikacích jazyka Visual Basic  
 Na serveru vytváření sestav technologie, která je součástí systému SQL Server Reporting Services je. Služba Reporting Services obsahuje další funkce, které nejsou součástí ovládací prvky prohlížeče sestav. Vyberte Reporting Services, pokud budete potřebovat některou z následujících funkcí:  
  
-   Nasazení scale-out a zpracování sestavy na straně serveru, který poskytuje Vylepšený výkon u složitých nebo dlouhodobě spuštěných sestav a pro sestavy vysoký počet aktivit.  
  
-   Integrované zpracování dat a sestav, s podporou pro ovládací prvky vlastních sestav a bohaté možnosti vykreslování formáty výstupu.  
  
-   Naplánované zpracování sestavy tak, aby je zadat přesně při spuštění sestavy.  
  
-   Sestava založená na předplatitele distribuce e-mailem nebo do umístění sdílené složky souborů.  
  
-   Vykazování ad hoc tak, aby obchodní uživatelé můžou vytvářet sestavy, podle potřeby.  
  
-   Odběry řízené daty, které směrovat výstup vlastních sestav dynamického seznamu příjemců.  
  
-   Vlastní rozšíření pro zpracování dat, způsob dodání sestavy, vlastní ověřování a vykreslování sestav.  
  
 Server sestav je implementovaný jako webová služba. Kód aplikace musí obsahovat volání webové služby pro přístup k sestavám a další metadata. Webová služba poskytuje kompletní programový přístup k instanci serveru sestav.  
  
 Vzhledem k tomu, že služby Reporting Services je webové technologie vytváření sestav, zobrazí výchozí prohlížeč sestav, které jsou generovány ve formátu HTML. Pokud nechcete použít jako výchozí formát prezentace sestav HTML, budete muset psát vlastní prohlížeč sestav pro vaši aplikaci.  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Vytváření sestav v sadě Visual Studio pro službu Reporting Services  
 K vytváření sestav, které běží na serveru sestav, vytvoříte definici sestavy (.rdl) soubory v sadě Visual Studio prostřednictvím Business Intelligence Development Studio, který je součástí systému SQL Server 2005.  
  
 Business Intelligence Development Studio přidá šablony projektu, které jsou specifické pro součásti systému SQL Server. Chcete-li vytvořit sestavy, můžete vybírat **projektů serveru sestav** nebo **Průvodce projekt serveru sestav** šablony. Můžete zadat připojení ke zdroji dat a dotazy na celou řadu typů zdrojů dat, včetně systému SQL Server, Oracle, Analysis Services, XML a SQL Server Integration Services. A **Data** kartě **rozložení** kartu, a **ve verzi Preview** kartu umožňují definovat data, vytvářet rozložení sestavy a zobrazit náhled sestavy všech ve stejném pracovním prostoru.  
  
 Definice sestav, které vytvoříte pro ovládací prvek nebo server sestav je možné využít v obou technologií.  
  
|Pokud chcete vytvořit sestavu, která běží na serveru sestav|  
|---|    
|1.  Na **souboru** nabídce zvolte **nový**.<br />     **Nový projekt** zobrazí se dialogové okno.<br />2.  V **typy projektů** podokně klikněte na tlačítko **projekty Business Intelligence**.<br />3.  V podokně šablony vyberte **projektů serveru sestav** nebo **Průvodce projekt serveru sestav**.|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>Pomocí ovládacích prvků prohlížeče sestav a SQL Server Reporting Services  
 Ovládací prvky prohlížeče sestav a SQL Server 2005 Reporting Services je možné společně v jedné aplikaci.  
  
-   Ovládací prvek prohlížeče sestav poskytuje prohlížeč, který se používá k zobrazení sestavy ve vaší aplikaci.  
  
-   Služba Reporting Services obsahuje sestavy a provádí veškeré zpracování na vzdáleném serveru.  
  
 Chcete-li zobrazit sestavy, které jsou uloženy a zpracovány na vzdáleném serveru sestav služby Reporting Services je možné nakonfigurovat ovládací prvek prohlížeče sestav. Tento typ konfigurace se nazývá *režim vzdáleného zpracování*. Ovládací prvek v režimu vzdáleného zpracování požadavků sestavu, která je uložena na serveru sestav vzdálené. Server sestav provádí veškeré zpracování sestavy, zpracování dat a vykreslování sestav. Dokončené, sestavené sestavy se vrátí do ovládacího prvku a zobrazí v oblasti zobrazení.  
  
 Sestavy, které běží na serveru sestav další podporu formáty exportu, implementace Parametrizace jiná sestava, použijte typ zdroje dat, které jsou podporovány serverem sestav a jsou přístupné prostřednictvím modelu autorizace na základě rolí na server sestav.  
  
 Pokud chcete použít režim vzdáleného zpracování, zadejte adresu URL a cesty k serveru sestav při konfiguraci ovládacího prvku ReportViewer.
