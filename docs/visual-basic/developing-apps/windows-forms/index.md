---
title: Základy formulářové aplikace Windows (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: cc40d7e10243f63040d7e4ad457aac0f9122b6ad
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590781"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Základy formulářové aplikace Windows (Visual Basic)
Důležitou součástí jazyka Visual Basic je schopnost vytvářet aplikace Windows Forms, které se spouštějí místně v počítačích uživatelů. Visual Studio můžete použít k vytvoření aplikace a uživatelské rozhraní pomocí Windows Forms. Aplikace modelu Windows Forms jsou založeny na třídách z <xref:System.Windows.Forms> oboru názvů.  
  
## <a name="designing-windows-forms-applications"></a>Navrhování Windows Forms aplikací  
 Windows Forms a aplikací služby Windows můžete vytvořit pomocí sady Visual Studio. Další informace naleznete v následujících tématech:  
  
- [Začínáme s Windows Forms](../../../framework/winforms/getting-started-with-windows-forms.md). Poskytuje informace o tom, jak vytvořit a program Windows Forms.  
   
- [Ovládací prvky Windows Forms](../../../framework/winforms/controls/index.md). Kolekce témat s podrobnostmi o použití ovládacích prvků Windows Forms.  
  
- [Aplikace služeb Windows](../../../framework/windows-services/index.md). Vypíše seznam témat, která popisují, jak se vytvářejí služby Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Vytváření bohatých, interaktivních uživatelských rozhraní  
 Windows Forms je chytrých klientských součástí rozhraní .NET Framework sadu spravované knihovny pro provádění běžných aplikačních úloh, jako je čtení a zápis do systému souborů. Použití vývojového prostředí, jako je Visual Studio, můžete vytvořit aplikace Windows Forms, které zobrazení informací, žádejte vstup od uživatele a komunikovat se vzdálenými počítači přes síť.  
  
 Ve Windows Forms formuláře je vizuální povrch, na kterém můžete zobrazit informace pro uživatele. Běžně vytváříte aplikace Windows Forms umístěním ovládacích prvků ve formulářích a vývoj odpovědi na akce uživatele, jako je například kliknutí myší nebo stisknutí kláves. A *ovládací prvek* je prvek diskrétní uživatelského rozhraní (UI), která zobrazuje data nebo přijímá vstupní data.  
  
### <a name="events"></a>Události  
 Když uživatel provede něco formuláře nebo jeden z jeho ovládacích prvků, vygeneruje událost. Vaše aplikace reaguje na tyto události pomocí kódu a zpracovává události, které se objeví. Další informace najdete v tématu [vytváření obslužných rutin událostí ve Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Ovládací prvky  
 Windows Forms obsahuje celou řadu ovládacích prvků, které můžete umístit na formulářích: ovládací prvky zobrazující textová pole, tlačítka, rozevírací seznamy, přepínačů a dokonce i webové stránky. Seznam všech ovládacích prvků, můžete použít ve formuláři, naleznete v tématu [ovládací prvky používané ve formulářích Windows](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Pokud existujícího ovládacího prvku nevyhovuje vašim potřebám, Windows Forms podporuje také vytváření vlastních pomocí vlastních ovládacích prvků <xref:System.Windows.Forms.UserControl> třídy.  
  
 Windows Forms obsahuje bohaté ovládací prvky uživatelského rozhraní, která emulují funkce v špičková aplikací, jako je Microsoft Office. Použití <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.MenuStrip> ovládacího prvku, můžete vytvořit panelů nástrojů a nabídek, které obsahují text a obrázky, zobrazují podnabídky a hostují jiné ovládací prvky, jako je například textová pole a pole se seznamem.  
  
 Pomocí Návrháře formulářů přetáhněte myší sady Visual Studio, můžete snadno vytvořit aplikace Windows Forms: stačí vybrat ovládací prvky s kurzorem a umístit je místo, kam chcete ve formuláři. Návrhář poskytuje nástroje, jako je například mřížka a "vodicí čáry" vzít si dělat starosti zarovnání ovládacích prvků. Ať už pomocí sady Visual Studio nebo kompilaci do příkazového řádku, můžete si <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> a <xref:System.Windows.Forms.SplitContainer> vytvářet pokročilé ovládací prvky formuláře rozložení s minimální čas a úsilí.  
  
### <a name="custom-ui-elements"></a>Vlastní prvky uživatelského rozhraní  
 Nakonec, pokud je nutné vytvořit vlastní vlastní elementy uživatelského rozhraní <xref:System.Drawing> obor názvů obsahuje všechny třídy, které potřebujete k vykreslení čar, kruhy a ostatním tvarům přímo na formuláři.  
  
 Podrobné informace o použití těchto funkcí naleznete v následujících tématech nápovědy.  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Vytvoření nové aplikace Windows Forms pomocí sady Visual Studio|[Kurz 1: Vytvoření prohlížeče obrázků](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|  
|Použití ovládacích prvků ve formulářích|[Postupy: Přidání ovládacích prvků do formulářů Windows](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Vytváření grafiky <xref:System.Drawing>|[Začínáme s programováním grafiky](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Vytvořit vlastní ovládací prvky|[Postupy: Dědit ze třídy UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Zobrazení a manipulace s daty  
 Mnoho aplikací se musí zobrazovat data z databáze nebo soubor XML, webové služby XML nebo jiný zdroj dat. Windows Forms poskytuje flexibilní ovládací prvek volána <xref:System.Windows.Forms.DataGridView> ovládací prvek pro vykreslení takové tabulková data v tradiční řádků a sloupců formátu tak, aby každá část data zabírá vlastní buňku. Pomocí <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit vzhled jednotlivé buňky, uzamknout libovolného řádků a sloupců na místě a zobrazit komplexní ovládací prvky do buněk, kromě jiných funkcí.  
  
 Připojení ke zdrojům dat přes síť je jednoduchou úlohou s inteligentní klienti Windows Forms. <xref:System.Windows.Forms.BindingSource> Komponentu, nově ve Windows Forms v sadě Visual Studio 2005 a [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)], představuje připojení ke zdroji dat a poskytuje metody pro vazby dat k ovládacím prvkům, přejděte na další a předchozí záznamy, Hromadná úprava záznamů a ukládání změny zpět do původního zdroje. <xref:System.Windows.Forms.BindingNavigator> Řízení poskytuje jednoduché rozhraní průběhu <xref:System.Windows.Forms.BindingSource> komponentu uživatelům přecházení mezi záznamy.  
  
### <a name="data-bound-controls"></a>Ovládací prvky vázané daty  
 Můžete vytvořit ovládací prvky vázané na data snadno pomocí okna zdrojů dat, který obsahuje zdroje dat, jako je například databází, webových služeb a objektů ve vašem projektu. Můžete vytvořit ovládací prvky vázané na data přetažením položek z tohoto okna do formuláře v projektu. Vám může také vytvořte datovou vazbu existujících ovládacích prvků na data přetažením objektů z okna zdroje dat na existující ovládací prvky.  
  
### <a name="settings"></a>Nastavení  
 Nastavení je jiného typu vytváření datových vazeb, které můžete spravovat ve Windows Forms. Většina chytrých klientských aplikací musí uchovávat některé informace o stavu za běhu, jako je například poslední známou velikost formuláře a zachovat data předvolba uživatele, jako je například výchozí umístění pro ukládání souborů. Nastavení aplikace funkcí řeší tyto požadavky tím, že poskytuje snadný způsob, jak ukládat oba typy nastavení v klientském počítači. Po definování pomocí sady Visual Studio nebo editor kódu, tato nastavení jsou zachována ve formátu XML a automaticky číst zpět do paměti v době běhu.  
  
 Podrobné informace o použití těchto funkcí naleznete v následujících tématech nápovědy.  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Použití <xref:System.Windows.Forms.BindingSource> komponenty|[Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí návrháře](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Práce s [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zdroje dat|[Postupy: Řazení a filtrování dat ADO.NET pomocí Windows Forms BindingSource – komponenta](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Použití okna zdroje dat|[Návod: Zobrazení dat ve formuláři Windows](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Nasazení aplikací na klientských počítačích  
 Jakmile jste napsali vaší aplikace, musíte odeslat uživatelům tak, že můžete nainstalovat a spustit ve svých počítačích klienta. Použití [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] technologie, můžete nasadit aplikace z Visual Studia pomocí pár kliknutí a uživatelům poskytnout adresu URL odkazující na aplikaci na webu. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] spravuje všechny elementy a závislosti v aplikaci a zajišťuje, že je aplikace správně nainstalován na klientském počítači.  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikace může být nakonfigurována na spustit, jenom když je uživatel se připojil k síti, nebo obě online i offline. Pokud určíte, že aplikace by měla podporovat operace vypnutí [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] přidá odkaz na vaši aplikaci v uživatele **Start** nabídky, tak, aby uživatel může otevřít bez pomocí adresy URL.  
  
 Když aktualizujete aplikaci, můžete publikovat nový manifest nasazení a novou kopii aplikace na webovém serveru. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] zjistí, že je k dispozici aktualizace a upgraduje instalaci uživatele. bez nutnosti programování se vyžaduje k aktualizaci staré sestavení.  
  
 Úplné Úvod k [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], naleznete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment). Podrobné informace o použití těchto funkcí naleznete v následujících tématech nápovědy:  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Nasazení aplikace pomocí [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Aktualizace [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nasazení|[Postupy: Správa aktualizací aplikace ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Správa zabezpečení se [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Postupy: Povolení nastavení zabezpečení ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Další ovládací prvky a funkce  
 Existuje mnoho dalších funkcí ve Windows Forms, který implementující běžné úkoly, rychlý a snadný, jako třeba podporu pro vytváření dialogových oken, tisk, přidání nápovědy a dokumentace a lokalizace aplikace pro více jazyků. Kromě toho Windows Forms závisí na systému robustní zabezpečení rozhraní .NET Framework, můžete vydat bezpečnější aplikací pro vaše zákazníky.  
  
 Podrobné informace o použití těchto funkcí naleznete v následujících tématech nápovědy:  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Vytisknout obsah formuláře|[Postupy: Tisk grafiky ve Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Postupy: Tisk vícestránkového textového souboru ve Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Další informace o Windows Forms – zabezpečení|[Přehled zabezpečení ve Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Přehled produktu Windows Forms](../../../framework/winforms/windows-forms-overview.md)
- [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
