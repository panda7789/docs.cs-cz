---
title: Přehled produktu Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 50c88aec8ac57be2ab317ac91464d68503607738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541723"
---
# <a name="windows-forms-overview"></a>Přehled produktu Windows Forms
V následujícím přehledu popisuje výhody inteligentní klientské aplikace, hlavní funkce programování modelu Windows Forms a použití Windows Forms k vytvoření inteligentní klienti, které naplňují potřeby pro podniky a koncoví uživatelé je aktuální.  
  
## <a name="windows-forms-and-smart-client-applications"></a>Windows Forms a inteligentní klientské aplikace  
 S Windows Forms vyvíjet inteligentní klienti. *Inteligentní klienti* graficky náročné aplikace, které se snadno nasadit a aktualizovat, můžete pracovat, pokud jsou připojené k nebo odpojení od Internetu a mají přístup k prostředkům v místním počítači způsobem bezpečnější než tradiční Aplikace pro systém Windows.  
  
### <a name="building-rich-interactive-user-interfaces"></a>Sestavování bohaté, interaktivní uživatelské rozhraní  
 Windows Forms je technologie inteligentní klienta pro [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], sadu spravovaných knihovny, které usnadňují běžné úkoly aplikace jako čtení a zápis do systému souborů. Pokud používáte prostředí pro vývoj jako v aplikaci Visual Studio, můžete vytvořit Windows Forms čipové klientských aplikací, které zobrazují informace, žádají vstup od uživatele a komunikovat se vzdálenými počítači přes síť.  
  
 V systému Windows Forms *formuláře* je visual plochy, na kterém je zobrazit informace o uživateli. Přidání ovládacích prvků do formulářů a vývoj odpovědi na akce uživatele, jako je například kliknutí myší nebo stisknutí klávesy vytvoříte běžným formulářových aplikací Windows. A *řízení* je element diskrétní uživatelské rozhraní (UI), který zobrazuje data nebo přijímá data vstup.  
  
 Když uživatel provede něco do svého formuláře nebo jeden z jeho ovládacích prvků, akce vygeneruje událost. Vaše aplikace reaguje na tyto události pomocí kódu a zpracovává události, když k nim dojde. Další informace najdete v tématu [vytváření obslužných rutin událostí v systému Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
 Windows Forms obsahuje řadu ovládacích prvků, které můžete přidat do formulářů: ovládací prvky, které zobrazují textová pole, tlačítka, rozevírací seznamy, přepínače a i webové stránky. Seznam všech ovládacích prvků, můžete použít ve formuláři najdete v tématu [ovládací prvky používané ve formulářích Windows](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Pokud ovládací prvek existující nevyhovuje vašim potřebám, Windows Forms také podporuje, vytváření vlastní vlastních ovládacích prvků pomocí <xref:System.Windows.Forms.UserControl> třídy.  
  
 Windows Forms má bohaté ovládací prvky uživatelského rozhraní, které emulují funkce v vyšší kategorie aplikace, jako je Microsoft Office. Při použití <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.MenuStrip> ovládací prvek, můžete vytvořit panely nástrojů a nabídky, které obsahují text, obrázky, zobrazují podnabídky a hostovat další ovládací prvky, jako je například textová pole a pole se seznamem.  
  
 Pomocí sady Visual Studio a přetažení Návrháře formulářů můžete snadno vytvořit formulářových aplikací Windows. Vyberte ovládací prvky s ukazatelem a přidat požadované místo na formuláři. Návrhář poskytuje nástroje, jako je například řádky mřížky a snap provést starostí zarovnání ovládacích prvků. A zda používáte Visual Studio nebo zkompilovat na příkazovém řádku, můžete použít <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> a <xref:System.Windows.Forms.SplitContainer> rozložení ovládacích prvků k vytvoření pokročilých na formulářích za kratší dobu.  
  
 Nakonec, pokud je nutné vytvořit vlastní vlastní elementy uživatelského rozhraní <xref:System.Drawing> obor názvů obsahuje velké výběr třídy k vykreslení čar, kružnice a ostatním tvarům přímo na formuláři.  
  
> [!NOTE]
>  Windows Forms – ovládací prvky nejsou navrženy být zařazena mezi doménami aplikace. Z tohoto důvodu Microsoft nepodporuje předávání ovládacího prvku Windows Forms napříč <xref:System.AppDomain> hranic, i když <xref:System.Windows.Controls.Control> základní typ <xref:System.MarshalByRefObject> by svědčit o tom, že je to možné. Windows Forms aplikace, které mají více domén aplikací jsou podporovány, pokud žádné Windows Forms – ovládací prvky jsou předávány mimo hranice domény aplikace.  
  
#### <a name="help-creating-forms-and-controls"></a>Vytváření formulářů a ovládací prvky  
 Podrobné informace o tom, jak tyto funkce používají najdete v následujících tématech nápovědy.  
  
|Popis|Téma nápovědy|  
|-----------------|----------------|  
|Použití ovládacích prvků ve formulářích|[Postupy: Přidávání ovládacích prvků do Windows Forms](../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|  
|Pomocí <xref:System.Windows.Forms.ToolStrip> ovládací prvek|[Postupy: Vytvoření základního prvku ToolStrip se standardními položkami pomocí Návrháře](../../../docs/framework/winforms/controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|  
|Vytváření grafických s <xref:System.Drawing>|[Začínáme s programováním grafiky](../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Vytváření vlastních ovládacích prvků|[Postupy: Dědění ze třídy UserControl](../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
### <a name="displaying-and-manipulating-data"></a>Zobrazení a manipulace s daty  
 Mnoho aplikací musí zobrazit data z databáze, soubor XML, webové služby XML nebo jiný zdroj dat. Windows Forms poskytuje flexibilní ovládací prvek s názvem <xref:System.Windows.Forms.DataGridView> ovládací prvek pro zobrazení tabulkových data v tradiční řádků a sloupců formátu, tak, aby každá část data nacházela vlastní buňku. Při použití <xref:System.Windows.Forms.DataGridView>, můžete přizpůsobit vzhled jednotlivých buněk, uzamknout libovolné řádků a sloupců v umístit a zobrazit komplexní ovládacích prvků do buněk mezi další funkce.  
  
 Připojení ke zdrojům dat přes síť je jednoduchou úlohou s inteligentní klienti Windows Forms. <xref:System.Windows.Forms.BindingSource> Součásti nové s Windows Forms v [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] a [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], představuje připojení ke zdroji dat a poskytuje metody pro vytvoření vazby dat s ovládacími prvky navigace na předchozí a další záznamy, úpravy záznamů a ukládání změny zpět do původního zdroje. <xref:System.Windows.Forms.BindingNavigator> Řízení poskytuje jednoduché rozhraní přes <xref:System.Windows.Forms.BindingSource> součásti přechody mezi záznamy.  
  
 Ovládací prvky vázané na data můžete jednoduše vytvořit pomocí okna zdroje dat. V okně se zobrazí zdroje dat, jako je například databáze, webové služby a objekty ve vašem projektu. Ovládací prvky vázané na data můžete vytvořit tak, že přetáhnete položky z tohoto okno do formuláře ve vašem projektu. Vám může také navázat existujících ovládacích prvků k datům přetažením objektů z okna zdroje dat do existujícího ovládacího prvku.  
  
 Jiný typ vazby dat, které můžete spravovat ve Windows Forms je *nastavení*. Většina inteligentní klientské aplikace musí zachovat určité informace o stavu jejich spuštění, například poslední známá velikost formuláře a zachovat data předvoleb uživatele, například výchozí umístění pro ukládání souborů. Funkce nastavení aplikace řeší tyto požadavky tím, že poskytuje snadný způsob, jak uložit oba typy nastavení v klientském počítači. Po definování těchto nastavení pomocí sady Visual Studio nebo editoru kódu, jsou nastavení uchován jako XML a automaticky načíst zpět do paměti v době běhu.  
  
#### <a name="help-displaying-and-manipulating-data"></a>Zobrazení nápovědy a manipulace s daty  
 Podrobné informace o tom, jak tyto funkce používají najdete v následujících tématech nápovědy.  
  
|Popis|Téma nápovědy|  
|-----------------|----------------|  
|Pomocí <xref:System.Windows.Forms.BindingSource> součásti|[Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře](../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Práce s [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] zdroje dat|[Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource](../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|  
|Pomocí okna zdroje dat|[Návod: Zobrazování dat ve formuláři Windows](http://msdn.microsoft.com/library/f6e08c2c-c792-43de-adf3-3e52c0100225)|  
|Pomocí nastavení aplikace|[Postupy: Vytváření nastavení aplikace](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)|  
  
### <a name="deploying-applications-to-client-computers"></a>Nasazení aplikací na klientských počítačích  
 Poté, co jste napsali vaší aplikace, je nutné odeslat aplikace uživatelům, aby můžete nainstalovat a spustit ji v klientských počítačích. Při použití [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] technologie, můžete nasadit aplikace z Visual Studia pomocí několika kliknutí a uživatelům poskytnout adresu URL odkazující na aplikaci na webu. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] spravuje všechny elementy a závislosti v aplikaci a zajistí, že je aplikace správně nainstalovat na klientském počítači.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikace může být nakonfigurována, spustit pouze když je uživatel připojený k síti, nebo pokud online nebo offline. Pokud určíte, že aplikace má podporovat offline operace [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] přidá odkaz na aplikaci v uživatele **spustit** nabídky. Uživatel pak můžete otevřít aplikaci bez pomocí adresy URL.  
  
 Při aktualizaci aplikace, můžete publikovat nový manifest nasazení a novou kopii aplikace na vašem webovém serveru. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] zjistí, že je k dispozici aktualizace, který se upgrade uživatele instalace; žádné další programování se vyžaduje k aktualizaci původního sestavení.  
  
#### <a name="help-deploying-clickonce-applications"></a>Pomůže nasazení aplikace ClickOnce  
 Pro úplnou Úvod do [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], najdete v části [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment). Podrobné informace o tom, jak tyto funkce používají najdete v následujících tématech nápovědy  
  
|Popis|Téma nápovědy|  
|-----------------|----------------|  
|Nasazení aplikace s použitím [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Aktualizace [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení|[Postupy: Správa aktualizací pro aplikaci ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Správa zabezpečení pomocí [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Postupy: Povolení nastavení zabezpečení ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
### <a name="other-controls-and-features"></a>Další ovládací prvky a funkce  
 Existuje mnoho dalších funkcí ve Windows Forms, který implementující běžné úlohy rychlý a snadný, jako je podpora pro vytváření dialogových oken, tisk, přidání nápovědy a dokumentace a lokalizace aplikace pro více jazyků. Kromě toho využívá robustní zabezpečení systému Windows Forms [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. K tomuto systému můžete vydat bezpečnější aplikací pro vaše zákazníky.  
  
#### <a name="help-implementing-other-controls-and-features"></a>Nápověda implementace další ovládací prvky a funkce  
 Podrobné informace o tom, jak tyto funkce používají najdete v následujících tématech nápovědy.  
  
|Popis|Téma nápovědy|  
|-----------------|----------------|  
|Tisk obsahu formuláře|[Postupy: Tisk grafiky v modelu Windows Forms](../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|  
|Další informace o zabezpečení Windows Forms|[Přehled zabezpečení ve Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Vytvoření nového formuláře Windows Forms](../../../docs/framework/winforms/creating-a-new-windows-form.md)  
 [Přehled ovládacího prvku ToolStrip](../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Přehled ovládacího prvku DataGridView](../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Přehled komponenty BindingSource](../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [Přehled nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
