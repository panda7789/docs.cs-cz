---
title: Základy formulářové aplikace Windows (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230229203029740b82e706fe2aa7ff8ee06c486a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="windows-forms-application-basics-visual-basic"></a>Základy formulářové aplikace Windows (Visual Basic)
Důležitou součástí jazyka Visual Basic je schopnost vytvářet aplikace Windows Forms, které běží místně na počítačích uživatelů. Visual Studio můžete použít k vytvoření aplikace a uživatelské rozhraní Windows Forms pomocí. Aplikace Windows Forms jsou založeny na třídy z <xref:System.Windows.Forms> oboru názvů.  
  
## <a name="designing-windows-forms-applications"></a>Navrhování Windows Forms aplikace  
 Windows Forms a aplikace služby systému Windows můžete vytvořit pomocí sady Visual Studio. Další informace naleznete v následujících tématech:  
  
-   [Začínáme s Windows Forms](../../../framework/winforms/getting-started-with-windows-forms.md). Poskytuje informace o tom, jak vytvořit a program Windows Forms.  
   
-   [Ovládací prvky Windows Forms](../../../framework/winforms/controls/index.md). Kolekce témat s podrobnostmi o použití ovládacích prvků Windows Forms.  
  
-   [Aplikace služby systému Windows](../../../framework/windows-services/index.md). Seznam témat, která popisují, jak vytváření služeb systému Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Sestavování bohaté, interaktivní uživatelské rozhraní  
 Windows Forms je komponenta čipové klienta [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], sadu spravovaných knihovny, které umožňují běžné úkoly aplikace jako čtení a zápis do systému souborů. Použití vývojového prostředí, jako v aplikaci Visual Studio, můžete vytvořit Windows Forms aplikace, které zobrazují informace, žádají vstup od uživatele a komunikaci se vzdálenými počítači přes síť.  
  
 V systému Windows Forms formulář je visual prostor, na kterém je zobrazit informace o uživateli. Běžně vytváříte aplikace Windows Forms podle umístění ovládacích prvků ve formulářích a vývoj odpovědi na akce uživatele, jako je například kliknutí myší nebo stisknutí klávesy. A *řízení* je element diskrétní uživatelské rozhraní (UI), který zobrazuje data nebo přijímá data vstup.  
  
### <a name="events"></a>Události  
 Když uživatel provede něco do svého formuláře nebo jeden z jeho ovládacích prvků, vygeneruje událost. Vaše aplikace reaguje na tyto události pomocí kódu a zpracovává události, když k nim dojde. Další informace najdete v tématu [vytváření obslužných rutin událostí v systému Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Ovládací prvky  
 Windows Forms obsahuje řadu ovládacích prvků, které můžete umístit na formulářích: ovládací prvky, které zobrazují textová pole, tlačítka, rozevírací seznamy, přepínače a i webové stránky. Seznam všech ovládacích prvků, můžete použít ve formuláři najdete v tématu [ovládací prvky používané ve formulářích Windows](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Pokud ovládací prvek existující nevyhovuje vašim potřebám, Windows Forms také podporuje, vytváření vlastní vlastních ovládacích prvků pomocí <xref:System.Windows.Forms.UserControl> třídy.  
  
 Windows Forms má bohaté ovládací prvky uživatelského rozhraní, které emulují funkce v vyšší kategorie aplikace, jako je Microsoft Office. Pomocí <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.MenuStrip> ovládací prvek, můžete vytvořit panely nástrojů a nabídky, které obsahují text, obrázky, zobrazují podnabídky a hostovat další ovládací prvky, jako je například textová pole a pole se seznamem.  
  
 Pomocí přetahování myší forms návrháře Visual Studio, můžete snadno vytvořit formulářových aplikací Windows: právě ovládací prvky s ukazatelem pro výběr a umístit je na místo na formuláři. Návrhář poskytuje nástroje, jako je například mřížky a "snap řádky" provést starostí zarovnání ovládacích prvků. A zda používáte Visual Studio nebo zkompilovat na příkazovém řádku, můžete použít <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> a <xref:System.Windows.Forms.SplitContainer> ovládací prvky pro vytvoření pokročilých rozložení s minimální čas a úsilí na formulářích.  
  
### <a name="custom-ui-elements"></a>Vlastní prvky uživatelského rozhraní  
 Nakonec, pokud je nutné vytvořit vlastní vlastní elementy uživatelského rozhraní <xref:System.Drawing> obor názvů obsahuje všechny třídy, které potřebujete k vykreslení čar, kružnice a ostatním tvarům přímo na formuláři.  
  
 Podrobné informace o použití těchto funkcí najdete v následujících tématech nápovědy.  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Vytvořte novou aplikaci Windows Forms pomocí sady Visual Studio|[Návod: Vytvoření jednoduché Windows Form](http://msdn.microsoft.com/library/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Použití ovládacích prvků ve formulářích|[Postupy: Přidávání ovládacích prvků do Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Vytváření grafiky s <xref:System.Drawing>|[Začínáme s programováním grafiky](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Vytvořit vlastní ovládací prvky|[Postupy: Dědění ze třídy UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Zobrazení a manipulace s daty  
 Mnoho aplikací musí zobrazit data z databáze, soubor XML, webové služby XML nebo jiný zdroj dat. Windows Forms poskytuje flexibilní ovládací <xref:System.Windows.Forms.DataGridView> řízení pro vykreslení tabulkových data v tradiční řádků a sloupců formátu, tak, aby každá část data nacházela vlastní buňku. Pomocí <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit vzhled jednotlivých buněk, zamknout libovolný řádků a sloupců v místě a zobrazit komplexní ovládacích prvků do buněk mezi další funkce.  
  
 Připojení ke zdrojům dat přes síť je jednoduchou úlohou s inteligentní klienti Windows Forms. <xref:System.Windows.Forms.BindingSource> Součásti nové s Windows Forms v [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] a [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)], představuje připojení ke zdroji dat a poskytuje metody pro vytvoření vazby dat s ovládacími prvky navigace na předchozí a další záznamy, úpravy záznamů a ukládání změny zpět do původního zdroje. <xref:System.Windows.Forms.BindingNavigator> Řízení poskytuje jednoduché rozhraní přes <xref:System.Windows.Forms.BindingSource> součásti přechody mezi záznamy.  
  
### <a name="data-bound-controls"></a>Ovládací prvky vázané na data  
 Můžete vytvořit ovládací prvky vázané na data snadno pomocí okna zdroje dat, která zobrazuje zdroje dat, jako je například databáze, webové služby a objekty ve vašem projektu. Ovládací prvky vázané na data můžete vytvořit tak, že přetáhnete položky z tohoto okno do formuláře ve vašem projektu. Vám může také navázat existujících ovládacích prvků k datům přetažením objektů z okna zdroje dat do existujícího ovládacího prvku.  
  
### <a name="settings"></a>Nastavení  
 Jiný typ vazby dat, které můžete spravovat ve Windows Forms, jsou nastavení. Většina inteligentních klientských aplikací musí zachovat určité informace o jejich stavu spuštění, jako je například velikost poslední známá formulářů a zachovat data předvolba uživatele, například výchozí umístění pro ukládání souborů. Funkce nastavení aplikace řeší tyto požadavky tím, že poskytuje snadný způsob, jak uložit oba typy nastavení v klientském počítači. Jakmile definovány pomocí sady Visual Studio nebo editoru kódu, tato nastavení jsou nastavené jako trvalé jako XML a automaticky načíst zpět do paměti v době běhu.  
  
 Podrobné informace o použití těchto funkcí najdete v následujících tématech nápovědy.  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Použití <xref:System.Windows.Forms.BindingSource> součásti|[Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Práce s [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zdroje dat|[Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|Použití okna zdroje dat|[Návod: Zobrazování dat ve formuláři Windows](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Nasazení aplikací na klientských počítačích  
 Jakmile jste napsali vaší aplikace, je nutné ji odeslat uživatelům, aby můžete nainstalovat a spustit ji v klientských počítačích. Pomocí [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] technologie, které můžete nasadit aplikace z Visual Studia pomocí několika kliknutí a uživatelům poskytnout adresu URL odkazující na aplikaci na webu. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] spravuje všechny elementy a závislosti v aplikaci a zajistí, že je aplikace správně nainstalovat na klientském počítači.  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikace může být nakonfigurována, spustit pouze když je uživatel připojený k síti, nebo pokud online nebo offline. Pokud určíte, že aplikace má podporovat offline operace [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] přidá odkaz na aplikaci v uživatele **spustit** nabídky, takže uživatel může otevřít bez pomocí adresy URL.  
  
 Při aktualizaci aplikace, můžete publikovat nový manifest nasazení a novou kopii aplikace na vašem webovém serveru. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] zjistí, že je k dispozici aktualizace a upgrady instalace uživatele; žádné další programování se vyžaduje k aktualizaci původního sestavení.  
  
 Pro úplnou Úvod do [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], najdete v části [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment). Podrobné informace o použití těchto funkcí najdete v následujících tématech nápovědy:  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Nasazení aplikace s [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Aktualizace [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nasazení|[Postupy: Správa aktualizací pro aplikaci ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Správa zabezpečení s [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Postupy: Povolení nastavení zabezpečení ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Další ovládací prvky a funkce  
 Existuje mnoho dalších funkcí ve Windows Forms, který implementující běžné úlohy rychlý a snadný, jako je podpora pro vytváření dialogových oken, tisk, přidání nápovědy a dokumentace a lokalizace aplikace pro více jazyků. Kromě toho využívá robustní zabezpečení systému Windows Forms [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], který vám umožňuje vytváření bezpečnější aplikací pro vaše zákazníky.  
  
 Podrobné informace o použití těchto funkcí najdete v následujících tématech nápovědy:  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Vytiskne obsah formuláře|[Postupy: Tisk grafiky v modelu Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Další informace o zabezpečení Windows Forms|[Přehled zabezpečení ve Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Přehled produktu Windows Forms](../../../framework/winforms/windows-forms-overview.md)  
 [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
