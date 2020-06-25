---
title: Přehled
description: Naučte se, jak můžete použít model Windows Forms k sestavení inteligentních klientů, kteří splňují potřeby současných podniků a koncových uživatelů.
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 820d5bae54ecb5a868314197d6a7e45e097b57de
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325982"
---
# <a name="windows-forms-overview"></a>Přehled model Windows Forms

Následující přehled popisuje výhody inteligentních klientských aplikací, hlavní funkce model Windows Forms programování a způsob, jakým můžete použít model Windows Forms k vytváření inteligentních klientů, kteří splňují potřeby současných podniků a koncových uživatelů.

## <a name="windows-forms-and-smart-client-apps"></a>model Windows Forms a inteligentní klientské aplikace

 Model Windows Forms vyvíjíte inteligentní klienty. *Inteligentní klienti* jsou graficky bohatých aplikací, které se dají snadno nasadit a aktualizovat, můžou fungovat, když jsou připojené k Internetu nebo se z něj odpojí a mají přístup k prostředkům v místním počítači bezpečnějším způsobem než tradiční aplikace založené na Windows.

### <a name="build-rich-interactive-user-interfaces"></a>Vytváření bohatých interaktivních uživatelských rozhraní

 Model Windows Forms je technologie inteligentního klienta pro .NET Framework, sadu spravovaných knihoven, které zjednodušují běžné aplikační úlohy, jako je čtení a zápis do systému souborů. Při použití vývojového prostředí, jako je Visual Studio, můžete vytvořit model Windows Forms aplikací pro inteligentní klienty, které zobrazují informace, vyžadovat vstup od uživatelů a komunikovat se vzdálenými počítači přes síť.

 V model Windows Forms je *formulář* vizuálním povrchem, na kterém se zobrazují informace pro uživatele. Můžete vytvářet aplikace model Windows Forms, a to přidáním ovládacích prvků do formulářů a vývojem reakcí na akce uživatelů, jako je kliknutí myší nebo stisknutí klávesových zkratek. *Ovládací prvek* je diskrétní prvky uživatelského rozhraní (UI), které zobrazuje data nebo přijímá vstupní data.

 Když uživatel provede nějaký formulář nebo některý z jeho ovládacích prvků, akce vygeneruje událost. Vaše aplikace reaguje na tyto události pomocí kódu a zpracovává události, když k nim dojde. Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](creating-event-handlers-in-windows-forms.md).

 Model Windows Forms obsahuje různé ovládací prvky, které lze přidat do formulářů: ovládací prvky, které zobrazují textová pole, tlačítka, rozevírací seznamy, přepínače a dokonce i webové stránky. Seznam všech ovládacích prvků, které lze použít na formuláři, naleznete v tématu [ovládací prvky pro použití v model Windows Forms](./controls/controls-to-use-on-windows-forms.md). Pokud existující ovládací prvek nevyhovuje vašim potřebám, model Windows Forms také podporuje vytváření vlastních ovládacích prvků pomocí <xref:System.Windows.Forms.UserControl> třídy.

 Model Windows Forms má bohatě řízené ovládací prvky uživatelského rozhraní, které emuluje funkce v špičkových aplikacích, jako je systém Microsoft Office. Při použití <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.MenuStrip> ovládacího prvku a můžete vytvořit panely nástrojů a nabídky, které obsahují text a obrázky, zobrazit podnabídky a hostovat další ovládací prvky, jako jsou textová pole a pole se seznamem.

 Při přetahování **Návrhář formulářů** v aplikaci Visual Studio můžete snadno vytvářet model Windows Forms aplikace. Stačí vybrat ovládací prvky s kurzorem a přidat je tam, kde chcete na formuláři. Návrhář poskytuje nástroje, jako jsou mřížky a přichycení řádků, aby se z zarovnání ovládacích prvků vybraly bez problémů. A bez ohledu na to, zda používáte aplikaci Visual Studio nebo zkompilujete na příkazovém řádku, můžete použít <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.SplitContainer> ovládací prvky a k vytváření pokročilých rozložení formulářů v kratší dobu.

 Nakonec, pokud je nutné vytvořit vlastní prvky uživatelského rozhraní, <xref:System.Drawing> obor názvů obsahuje velký výběr tříd pro vykreslení čar, kruhů a dalších tvarů přímo na formuláři.

> [!NOTE]
> Ovládací prvky model Windows Forms nejsou určeny k zařazování mezi doménami aplikace. Z tohoto důvodu společnost Microsoft nepodporuje předávání ovládacího prvku model Windows Forms přes <xref:System.AppDomain> hranici, i když <xref:System.Windows.Controls.Control> základní typ <xref:System.MarshalByRefObject> by mohl indikovat, že je to možné. Model Windows Forms aplikace, které mají více aplikačních domén, jsou podporovány, pokud žádné model Windows Forms ovládací prvky nejsou předány napříč hranicemi aplikační domény.

#### <a name="create-forms-and-controls"></a>Vytváření formulářů a ovládacích prvků

Podrobné informace o tom, jak tyto funkce používat, najdete v následujících tématech nápovědy.

|Popis|Téma nápovědy|
|-----------------|----------------|
|Používání ovládacích prvků ve formulářích|[Postupy: Přidávání ovládacích prvků do formulářů Windows](./controls/how-to-add-controls-to-windows-forms.md)|
|Použití <xref:System.Windows.Forms.ToolStrip> ovládacího prvku|[Postupy: Vytvoření základního prvku ToolStrip se standardními položkami pomocí Návrháře](./controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|
|Vytváření grafiky pomocí<xref:System.Drawing>|[Začínáme s programováním grafiky](./advanced/getting-started-with-graphics-programming.md)|
|Vytváření vlastních ovládacích prvků|[Postupy: Dědění ze třídy UserControl](./controls/how-to-inherit-from-the-usercontrol-class.md)|

### <a name="display-and-manipulate-data"></a>Zobrazení a manipulace s daty
 Mnoho aplikací musí zobrazovat data z databáze, souboru XML, webové služby XML nebo jiného zdroje dat. Model Windows Forms poskytuje flexibilní ovládací prvek, který se jmenuje <xref:System.Windows.Forms.DataGridView> ovládací prvek pro zobrazování takových tabulkových dat v tradičním formátu řádků a sloupců, takže každá část dat zabírá svou vlastní buňku. Když použijete <xref:System.Windows.Forms.DataGridView> , můžete přizpůsobit vzhled jednotlivých buněk, zamknout libovolné řádky a sloupce na místě a zobrazovat komplexní ovládací prvky uvnitř buněk, mimo jiné funkce.

 Připojení ke zdrojům dat přes síť je jednoduchý úkol s model Windows Forms inteligentními klienty. <xref:System.Windows.Forms.BindingSource>Komponenta představuje připojení ke zdroji dat a zpřístupňuje metody pro svázání dat s ovládacími prvky, přechod na předchozí a další záznamy, úpravy záznamů a uložení změn zpět do původního zdroje. <xref:System.Windows.Forms.BindingNavigator>Ovládací prvek poskytuje jednoduché rozhraní nad <xref:System.Windows.Forms.BindingSource> komponentou pro uživatele, kteří chtějí procházet záznamy.

 Ovládací prvky vázané na data lze snadno vytvořit pomocí okna zdroje dat. V okně se zobrazí zdroje dat, jako jsou databáze, webové služby a objekty v projektu. Můžete vytvořit ovládací prvky vázané na data přetažením položek z tohoto okna do formulářů v projektu. Můžete také datově navazovat existující ovládací prvky na data přetažením objektů z okna zdroje dat do existujících ovládacích prvků.

 Další typ datové vazby, který můžete spravovat v model Windows Forms, je *Nastavení*. Většina inteligentních klientských aplikací musí uchovávat nějaké informace o stavu za běhu, jako je například Poslední známá velikost formulářů, a uchovávat data předvoleb uživatele, například výchozí umístění pro uložené soubory. Funkce nastavení aplikace řeší tyto požadavky tím, že poskytuje snadný způsob, jak uložit oba typy nastavení v klientském počítači. Po definování těchto nastavení pomocí sady Visual Studio nebo editoru kódu jsou nastavení trvalá jako XML a automaticky se čtou zpátky do paměti v době běhu.

#### <a name="display-and-manipulate-data"></a>Zobrazení a manipulace s daty

Podrobné informace o tom, jak tyto funkce používat, najdete v následujících tématech nápovědy.

|Popis|Téma nápovědy|
|-----------------|----------------|
|Použití <xref:System.Windows.Forms.BindingSource> komponenty|[Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře](./controls/bind-wf-controls-with-the-bindingsource.md)|
|Práce s ADO.NET zdroji dat|[Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource](./controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Používání okna zdroje dat|[Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)|
|Použití nastavení aplikace|[Postupy: Vytváření nastavení aplikace](./advanced/how-to-create-application-settings.md)|

### <a name="deploy-apps-to-client-computers"></a>Nasazení aplikací do klientských počítačů

Po dokončení zápisu aplikace je nutné aplikaci odeslat uživatelům, aby ji mohli nainstalovat a spustit na jejich vlastních klientských počítačích. Při použití technologie ClickOnce můžete své aplikace nasadit z aplikace Visual Studio pomocí několika kliknutí myší a poskytnout uživatelům adresu URL odkazující na vaši aplikaci na webu. ClickOnce spravuje všechny prvky a závislosti v aplikaci a zajišťuje, že je aplikace správně nainstalována na klientském počítači.

Aplikace ClickOnce se dají nakonfigurovat tak, aby se spouštěly jenom v případě, že je uživatel připojený k síti, nebo aby běžel online i offline. Pokud určíte, že aplikace by měla podporovat offline operaci, ClickOnce přidá odkaz na vaši aplikaci v nabídce **Start** uživatele. Uživatel pak může aplikaci otevřít bez použití adresy URL.

Při aktualizaci aplikace publikujete nový manifest nasazení a novou kopii vaší aplikace na webový server. ClickOnce zjistí, že je k dispozici aktualizace, a upgraduje instalaci uživatele. k aktualizaci starých sestavení není nutné žádné vlastní programování.

#### <a name="deploy-clickonce-apps"></a>Nasazení aplikací ClickOnce

Úplný Úvod do technologie ClickOnce naleznete v tématu [zabezpečení a nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Podrobné informace o tom, jak tyto funkce používat, najdete v následujících tématech nápovědy:

|Popis|Téma nápovědy|
|-----------------|----------------|
|Nasazení aplikace pomocí technologie ClickOnce|[Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Aktualizace nasazení ClickOnce|[Postupy: Správa aktualizací pro aplikaci ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Správa zabezpečení pomocí technologie ClickOnce|[Postupy: Povolení nastavení zabezpečení ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

### <a name="other-controls-and-features"></a>Další ovládací prvky a funkce

V model Windows Forms existuje mnoho dalších funkcí, které umožňují rychle a snadno implementovat běžné úlohy, jako je podpora pro vytváření dialogových oken, tisk, přidání nápovědu a dokumentace a lokalizace aplikace do více jazyků. Kromě toho model Windows Forms spoléhá na robustní bezpečnostní systém .NET Framework. V tomto systému můžete zákazníkům uvolnit bezpečnější aplikace.

#### <a name="implement-other-controls-and-features"></a>Implementace dalších ovládacích prvků a funkcí

Podrobné informace o tom, jak tyto funkce používat, najdete v následujících tématech nápovědy.

|Popis|Téma nápovědy|
|-----------------|----------------|
|Tisk obsahu formuláře|[Postupy: Tisk grafiky v modelu Windows Forms](./advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](./advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Další informace o model Windows Forms zabezpečení|[Přehled zabezpečení ve Windows Forms](security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Viz také

- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
- [Vytvoření nového formuláře Windows Form](creating-a-new-windows-form.md)
- [ToolStrip – přehled ovládacího prvku](./controls/toolstrip-control-overview-windows-forms.md)
- [DataGridView – přehled ovládacího prvku](./controls/datagridview-control-overview-windows-forms.md)
- [BindingSource – přehled komponenty](./controls/bindingsource-component-overview.md)
- [Přehled nastavení aplikace](./advanced/application-settings-overview.md)
- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
