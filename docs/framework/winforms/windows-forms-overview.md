---
title: Přehled produktu Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 08e85828451ba6c66b13ff31e3d6c106871b8154
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875888"
---
# <a name="windows-forms-overview"></a>Přehled produktu Windows Forms

Následující přehled popisuje výhody inteligentní klientské aplikace, hlavní funkce programování formulářů Windows a jak můžete pomocí Windows Forms vytvářet inteligentní klienti, kteří splňují požadavky dnešních podniky a koncové uživatele.

## <a name="windows-forms-and-smart-client-apps"></a>Windows Forms a inteligentní klientské aplikace

 Windows Forms vám vytvářet inteligentní klienti. *Inteligentní klienti* jsou graficky náročné aplikace, které se dají snadno nasadit a aktualizovat, můžete pracovat, když jsou připojené k nebo odpojení od Internetu a způsobem bezpečnější než tradiční přístup k prostředkům v místním počítači Aplikace pro systém Windows.

### <a name="build-rich-interactive-user-interfaces"></a>Vytváření bohatých, interaktivních uživatelských rozhraní

 Windows Forms je technologie inteligentní klienta pro rozhraní .NET Framework, sadu spravované knihovny, které zjednodušují běžné úkoly v aplikaci jako je čtení a zápis do systému souborů. Při použití vývojového prostředí, jako je Visual Studio můžete vytvořit Windows Forms chytrých klientských aplikací, které zobrazují informace, žádejte vstup od uživatele a komunikovat se vzdálenými počítači přes síť.

 Ve Windows Forms *formuláře* je vizuální povrch, na kterém můžete zobrazit informace pro uživatele. Obvykle vytvoříte aplikace Windows Forms přidáním ovládacích prvků do formulářů a vývoj odpovědi na akce uživatele, jako je například kliknutí myší nebo stisknutí kláves. A *ovládací prvek* je prvek diskrétní uživatelského rozhraní (UI), která zobrazuje data nebo přijímá vstupní data.

 Když uživatel provede něco formuláře nebo jeden z jeho ovládacích prvků, akce vygeneruje událost. Vaše aplikace reaguje na tyto události pomocí kódu a zpracovává události, které se objeví. Další informace najdete v tématu [vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md).

 Windows Forms obsahuje celou řadu ovládacích prvků, které můžete přidat do formuláře: ovládací prvky zobrazující textová pole, tlačítka, rozevírací seznamy, přepínačů a dokonce i webové stránky. Seznam všech ovládacích prvků, můžete použít ve formuláři, naleznete v tématu [ovládací prvky používané ve formulářích Windows](./controls/controls-to-use-on-windows-forms.md). Pokud existujícího ovládacího prvku nevyhovuje vašim potřebám, Windows Forms podporuje také vytváření vlastních pomocí vlastních ovládacích prvků <xref:System.Windows.Forms.UserControl> třídy.

 Windows Forms obsahuje bohaté ovládací prvky uživatelského rozhraní, která emulují funkce v špičková aplikací, jako je Microsoft Office. Při použití <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.MenuStrip> ovládacího prvku, můžete vytvořit panelů nástrojů a nabídek, které obsahují text a obrázky, zobrazují podnabídky a hostují jiné ovládací prvky, jako je například textová pole a pole se seznamem.

 S přetahování myší **Návrháře formulářů Windows** v sadě Visual Studio, můžete snadno vytvořit aplikace Windows Forms. Stačí vybrat ovládací prvky s kurzorem a přidáním, kam chcete ve formuláři. Návrhář poskytuje nástroje, jako je například řádky mřížky a funkce přichycení k Usnadněte si zarovnání ovládacích prvků. Ať už pomocí sady Visual Studio nebo kompilaci do příkazového řádku, můžete si <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> a <xref:System.Windows.Forms.SplitContainer> vytvářet pokročilé ovládací prvky formuláře rozložení v kratším čase.

 Nakonec, pokud je nutné vytvořit vlastní vlastní elementy uživatelského rozhraní <xref:System.Drawing> obor názvů obsahuje široké škály třídy k vykreslení čar, kruhy a ostatním tvarům přímo na formuláři.

> [!NOTE]
> Ovládací prvky Windows Forms nejsou určeny k zařazen napříč doménami aplikace. Z tohoto důvodu Microsoft nepodporuje předávání ovládacího prvku Windows Forms v <xref:System.AppDomain> hranic, i když <xref:System.Windows.Controls.Control> základní typ <xref:System.MarshalByRefObject> by zdá se, že k označení, že je to možné. Tak dlouho, dokud žádné ovládací prvky Windows Forms jsou předány přes hranice aplikační domény, jsou podporovány aplikací Windows Forms, které mají více domén aplikace.

#### <a name="create-forms-and-controls"></a>Vytvoření formuláře a ovládací prvky

Podrobné informace o tom, jak používat tyto funkce najdete v následujících tématech nápovědy.

|Popis|Téma nápovědy|
|-----------------|----------------|
|Použití ovládacích prvků ve formulářích|[Postupy: Přidání ovládacích prvků do formulářů Windows](./controls/how-to-add-controls-to-windows-forms.md)|
|Použití <xref:System.Windows.Forms.ToolStrip> ovládacího prvku|[Postupy: Vytvoření základního prvku ToolStrip se standardními položkami pomocí návrháře](./controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|
|Vytvářet grafické obrazce s <xref:System.Drawing>|[Začínáme s programováním grafiky](./advanced/getting-started-with-graphics-programming.md)|
|Vytváření vlastních ovládacích prvků|[Postupy: Dědit ze třídy UserControl](./controls/how-to-inherit-from-the-usercontrol-class.md)|

### <a name="display-and-manipulate-data"></a>Zobrazit a pracovat s daty
 Mnoho aplikací se musí zobrazovat data z databáze nebo soubor XML, webové služby XML nebo jiný zdroj dat. Windows Forms poskytuje flexibilní ovládací prvek, který je pojmenován <xref:System.Windows.Forms.DataGridView> ovládací prvek pro zobrazení těchto tabulková data v tradiční řádků a sloupců formátu tak, aby každá část data zabírá vlastní buňku. Při použití <xref:System.Windows.Forms.DataGridView>, můžete přizpůsobit vzhled jednotlivé buňky, uzamčení libovolné řádky a sloupce v umístit a zobrazit komplexní ovládací prvky do buněk, kromě jiných funkcí.

 Připojení ke zdrojům dat přes síť je jednoduchou úlohou s inteligentní klienti Windows Forms. <xref:System.Windows.Forms.BindingSource> Komponenty představuje připojení ke zdroji dat a zveřejňuje metody pro vazby dat k ovládacím prvkům, přejděte na další a předchozí záznamy, Hromadná úprava záznamů a ukládají se změny zpět do původního zdroje. <xref:System.Windows.Forms.BindingNavigator> Řízení poskytuje jednoduché rozhraní průběhu <xref:System.Windows.Forms.BindingSource> komponentu uživatelům přecházení mezi záznamy.

 Ovládací prvky vázané na data můžete snadno vytvořit pomocí okna zdrojů dat. V okně zobrazí zdroje dat, jako je například databází, webových služeb a objektů ve vašem projektu. Můžete vytvořit ovládací prvky vázané na data přetažením položek z tohoto okna do formuláře v projektu. Vám může také vytvořte datovou vazbu existujících ovládacích prvků na data přetažením objektů z okna zdroje dat na existující ovládací prvky.

 Je jiný typ vázání dat můžete spravovat ve Windows Forms *nastavení*. Většina aplikací inteligentní klienta musí uchovávat některé informace o stavu za běhu, jako je například poslední známou velikost formuláře a zachovat data předvoleb uživatele, jako je například výchozí umístění pro ukládání souborů. Nastavení aplikace funkcí řeší tyto požadavky tím, že poskytuje snadný způsob, jak ukládat oba typy nastavení v klientském počítači. Po definování těchto nastavení s použitím sady Visual Studio nebo editor kódu, nastavení jsou zachována ve formátu XML a automaticky číst zpět do paměti v době běhu.

#### <a name="display-and-manipulate-data"></a>Zobrazit a pracovat s daty

Podrobné informace o tom, jak používat tyto funkce najdete v následujících tématech nápovědy.

|Popis|Téma nápovědy|
|-----------------|----------------|
|Použití <xref:System.Windows.Forms.BindingSource> komponenty|[Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí návrháře](./controls/bind-wf-controls-with-the-bindingsource.md)|
|Práce se zdroji dat ADO.NET|[Postupy: Řazení a filtrování dat ADO.NET pomocí Windows Forms BindingSource – komponenta](./controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Pomocí okna zdrojů dat|[Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)|
|Pomocí nastavení aplikace|[Postupy: Vytvořit nastavení aplikace](./advanced/how-to-create-application-settings.md)|

### <a name="deploy-apps-to-client-computers"></a>Nasazení aplikace do klientských počítačů

Poté, co jste napsali vaší aplikace, je nutné odeslat aplikaci pro vaše uživatele tak, že můžete nainstalovat a spustit ve svých počítačích klienta. Při použití [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] technologie, můžete nasadit aplikace z Visual Studia pomocí pár kliknutí a uživatelům poskytnout adresu URL odkazující na aplikaci na webu. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] spravuje všechny elementy a závislosti v aplikaci a zajišťuje, že je aplikace správně nainstalován na klientském počítači.

[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikace může být nakonfigurována na spustit, jenom když je uživatel se připojil k síti, nebo obě online i offline. Pokud určíte, že aplikace by měla podporovat operace vypnutí [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] přidá odkaz na vaši aplikaci v uživatele **Start** nabídky. Uživatel pak můžete otevřít aplikaci bez použití adresy URL.

Když aktualizujete aplikaci, můžete publikovat nový manifest nasazení a novou kopii aplikace na webovém serveru. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] zjistí, že je k dispozici aktualizace a upgradovat instalaci uživatele. bez nutnosti programování se vyžaduje k aktualizaci staré sestavení.

#### <a name="deploy-clickonce-apps"></a>Nasazení aplikací ClickOnce

Úplné Úvod k [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], naleznete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment). Podrobné informace o tom, jak používat tyto funkce najdete v následujících tématech nápovědy

|Popis|Téma nápovědy|
|-----------------|----------------|
|Nasazení aplikace s použitím [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Aktualizuje se [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení|[Postupy: Správa aktualizací aplikace ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Správa zabezpečení pomocí [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Postupy: Povolení nastavení zabezpečení ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

### <a name="other-controls-and-features"></a>Další ovládací prvky a funkce

Existuje mnoho dalších funkcí ve Windows Forms, který implementující běžné úkoly, rychlý a snadný, jako třeba podporu pro vytváření dialogových oken, tisk, přidání nápovědy a dokumentace a lokalizace aplikace pro více jazyků. Kromě toho Windows Forms závisí na systému robustní zabezpečení rozhraní .NET Framework. S tímto systémem můžete uvolnit bezpečnější aplikací pro vaše zákazníky.

#### <a name="implement-other-controls-and-features"></a>Implementovat další ovládací prvky a funkce

Podrobné informace o tom, jak používat tyto funkce najdete v následujících tématech nápovědy.

|Popis|Téma nápovědy|
|-----------------|----------------|
|Tisk obsahu formuláře|[Postupy: Tisk grafiky ve Windows Forms](./advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Postupy: Tisk vícestránkového textového souboru ve Windows Forms](./advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Další informace o Windows Forms – zabezpečení|[Přehled zabezpečení ve Windows Forms](security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Viz také:

- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
- [Vytvoření nového formuláře Windows Forms](creating-a-new-windows-form.md)
- [Přehled ovládacího prvku ToolStrip](./controls/toolstrip-control-overview-windows-forms.md)
- [Přehled ovládacího prvku DataGridView](./controls/datagridview-control-overview-windows-forms.md)
- [Přehled komponenty BindingSource](./controls/bindingsource-component-overview.md)
- [Přehled nastavení aplikace](./advanced/application-settings-overview.md)
- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
