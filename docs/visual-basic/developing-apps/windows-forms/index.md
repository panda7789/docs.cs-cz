---
title: Základy aplikací modelu Windows Forms
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: 1aa1edf0130e388c6cc87662d83591f41a8e2325
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349154"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Základy formulářové aplikace Windows (Visual Basic)

Důležitou součástí Visual Basic je schopnost vytvářet model Windows Forms aplikace, které se spouštějí místně na počítačích uživatelů. Pomocí sady Visual Studio můžete vytvořit aplikaci a uživatelské rozhraní pomocí model Windows Forms. Model Windows Forms aplikace je postavená na třídách z <xref:System.Windows.Forms> oboru názvů.

## <a name="designing-windows-forms-applications"></a>Navrhování model Windows Formsch aplikací

Pomocí sady Visual Studio můžete vytvářet aplikace model Windows Forms a služby pro Windows. Další informace najdete v následujících tématech:

- [Začínáme s model Windows Forms](../../../framework/winforms/getting-started-with-windows-forms.md). Poskytuje informace o tom, jak vytvořit a programovat model Windows Forms.

- [Ovládací prvky model Windows Forms](../../../framework/winforms/controls/index.md). Kolekce témat s podrobnostmi o použití ovládacích prvků model Windows Forms.

- [Aplikace služby systému Windows](../../../framework/windows-services/index.md). Obsahuje témata, která vysvětlují, jak vytvořit služby systému Windows.

## <a name="building-rich-interactive-user-interfaces"></a>Vytváření bohatých interaktivních uživatelských rozhraní

Model Windows Forms je komponentou inteligentního klienta v .NET Framework, sada spravovaných knihoven, které umožňují běžné aplikační úlohy, jako je čtení a zápis do systému souborů. Pomocí vývojového prostředí, jako je Visual Studio, můžete vytvářet model Windows Forms aplikace, které zobrazují informace, vyžadují vstup od uživatelů a komunikují se vzdálenými počítači přes síť.

V model Windows Forms je formulář vizuálním povrchem, na kterém se zobrazují informace pro uživatele. Můžete často sestavovat model Windows Forms aplikace tím, že umístíte ovládací prvky na formuláře a vystavíte reakce na akce uživatelů, jako je kliknutí myší nebo stisknutí klávesových zkratek. *Ovládací prvek* je diskrétní prvky uživatelského rozhraní (UI), které zobrazuje data nebo přijímá vstupní data.

### <a name="events"></a>Události

Když uživatel provede nějaký formulář nebo některý z jeho ovládacích prvků, vygeneruje událost. Vaše aplikace reaguje na tyto události pomocí kódu a zpracovává události, když k nim dojde. Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).

### <a name="controls"></a>Ovládací prvky

Model Windows Forms obsahuje různé ovládací prvky, které lze umístit do formulářů: ovládací prvky, které zobrazují textová pole, tlačítka, rozevírací seznamy, přepínače a dokonce i webové stránky. Seznam všech ovládacích prvků, které lze použít na formuláři, naleznete v tématu [ovládací prvky pro použití v model Windows Forms](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Pokud existující ovládací prvek nevyhovuje vašim potřebám, model Windows Forms také podporuje vytváření vlastních ovládacích prvků pomocí <xref:System.Windows.Forms.UserControl> třídy.

Model Windows Forms má bohatě řízené ovládací prvky uživatelského rozhraní, které emuluje funkce v špičkových aplikacích, jako je systém Microsoft Office. Pomocí ovládacího <xref:System.Windows.Forms.ToolStrip> prvku <xref:System.Windows.Forms.MenuStrip> a můžete vytvořit panely nástrojů a nabídky, které obsahují text a obrázky, zobrazit podnabídky a hostovat další ovládací prvky, jako jsou textová pole a pole se seznamem.

Pomocí Návrháře formulářů přetahování sady Visual Studio můžete snadno vytvářet model Windows Forms aplikace: stačí vybrat ovládací prvky s kurzorem a umístit je tam, kde chcete na formuláři. Návrhář poskytuje nástroje, jako jsou čáry mřížky a "přichycení čáry", aby bylo možné z zarovnání ovládacích prvků zabrat jakékoli potíže. A bez ohledu na to, zda používáte aplikaci Visual Studio nebo zkompilovat na příkazovém řádku, <xref:System.Windows.Forms.FlowLayoutPanel>můžete <xref:System.Windows.Forms.TableLayoutPanel> použít <xref:System.Windows.Forms.SplitContainer> ovládací prvky a a vytvořit tak rozšířená rozložení formulářů s minimálním časem a úsilím.

### <a name="custom-ui-elements"></a>Vlastní prvky uživatelského rozhraní

Nakonec, pokud je nutné vytvořit vlastní prvky uživatelského rozhraní, <xref:System.Drawing> obor názvů obsahuje všechny třídy, které potřebujete k vykreslování čar, kruhů a dalších tvarů přímo na formuláři.

Podrobné informace o používání těchto funkcí najdete v následujících tématech nápovědy.

|Akce|Seznamte se s |
|--------|---------|
|Vytvoření nové aplikace model Windows Forms pomocí sady Visual Studio|[Kurz 1: vytvoření prohlížeče obrázků](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|
|Použití ovládacích prvků ve formulářích|[Postupy: Přidávání ovládacích prvků do formulářů Windows](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|
|Vytváření grafiky pomocí<xref:System.Drawing>|[Začínáme s programováním grafiky](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|
|Vytváření vlastních ovládacích prvků|[Postupy: Dědění ze třídy UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|

## <a name="displaying-and-manipulating-data"></a>Zobrazení dat a manipulace s nimi

Mnoho aplikací musí zobrazovat data z databáze, souboru XML, webové služby XML nebo jiného zdroje dat. Model Windows Forms poskytuje flexibilní ovládací prvek, který <xref:System.Windows.Forms.DataGridView> se nazývá ovládací prvek pro vykreslování takových tabulkových dat v tradičním formátu řádku a sloupce, aby každá část dat zabírala svoji vlastní buňku. Pomocí <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit vzhled jednotlivých buněk, zamknout libovolné řádky a sloupce na místě a zobrazovat komplexní ovládací prvky uvnitř buněk mimo jiné funkce.

Připojení ke zdrojům dat přes síť je jednoduchý úkol s model Windows Forms inteligentními klienty. <xref:System.Windows.Forms.BindingSource> Součást, novinka s model Windows Forms v aplikaci Visual Studio 2005 a .NET Framework 2,0 představuje připojení ke zdroji dat a zpřístupňuje metody pro svázání dat s ovládacími prvky, přechod na předchozí a další záznamy, úpravy záznamů a uložení změn zpět do původního zdroje. <xref:System.Windows.Forms.BindingNavigator> Ovládací prvek poskytuje jednoduché rozhraní nad <xref:System.Windows.Forms.BindingSource> komponentou pro uživatele, kteří chtějí procházet záznamy.

### <a name="data-bound-controls"></a>Ovládací prvky vázané na data

Můžete snadno vytvářet ovládací prvky vázané na data pomocí okna zdroje dat, které zobrazuje zdroje dat, jako jsou databáze, webové služby a objekty v projektu. Můžete vytvořit ovládací prvky vázané na data přetažením položek z tohoto okna do formulářů v projektu. Můžete také datově navazovat existující ovládací prvky na data přetažením objektů z okna zdroje dat do existujících ovládacích prvků.

### <a name="settings"></a>Nastavení

Další typ datové vazby, který můžete spravovat v model Windows Forms, je nastavení. Většina inteligentních klientských aplikací musí uchovávat nějaké informace o stavu běhu, jako je například Poslední známá velikost formulářů, a uchovávat data předvoleb uživatele, jako jsou například výchozí umístění pro uložené soubory. Funkce nastavení aplikace řeší tyto požadavky tím, že poskytuje snadný způsob, jak uložit oba typy nastavení v klientském počítači. Po definování pomocí sady Visual Studio nebo editoru kódu jsou tato nastavení trvalá jako XML a automaticky se čtou zpátky do paměti v době běhu.

Podrobné informace o používání těchto funkcí najdete v následujících tématech nápovědy.

|Akce|Seznamte se s |
|--------|---------|
|Použití <xref:System.Windows.Forms.BindingSource> komponenty|[Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|
|Práce s ADO.NETmi zdroji dat|[Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Použití okna zdroje dat|[Návod: zobrazení dat ve formuláři Windows](/visualstudio/data-tools/accessing-data-in-visual-studio)|

## <a name="deploying-applications-to-client-computers"></a>Nasazení aplikací do klientských počítačů

Po napsání aplikace ji musíte odeslat uživatelům, aby ji mohli nainstalovat a spustit na jejich vlastních klientských počítačích. Pomocí technologie ClickOnce můžete své aplikace nasadit z aplikace Visual Studio pomocí několika kliknutí a poskytnout uživatelům adresu URL, která odkazuje na vaši aplikaci na webu. ClickOnce spravuje všechny prvky a závislosti v aplikaci a zajišťuje, že je aplikace správně nainstalována na klientském počítači.

Aplikace ClickOnce se dají nakonfigurovat tak, aby se spouštěly jenom v případě, že je uživatel připojený k síti, nebo aby běžel online i offline. Pokud určíte, že aplikace by měla podporovat offline operaci, ClickOnce přidá odkaz na vaši aplikaci v nabídce **Start** uživatele, aby ji uživatel mohl otevřít bez použití adresy URL.

Při aktualizaci aplikace publikujete nový manifest nasazení a novou kopii vaší aplikace na webový server. ClickOnce detekuje, že je k dispozici aktualizace a upgraduje instalaci uživatele. k aktualizaci starých sestavení není nutné žádné vlastní programování.

Úplný Úvod do technologie ClickOnce naleznete v tématu [zabezpečení a nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Podrobné informace o používání těchto funkcí najdete v následujících tématech nápovědy:

|Akce|Seznamte se s |
|--------|---------|
|Nasazení aplikace pomocí technologie ClickOnce|[Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Aktualizace ClickOnce nasazení|[Postupy: Správa aktualizací pro aplikaci ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Správa zabezpečení pomocí technologie ClickOnce|[Postupy: Povolení nastavení zabezpečení ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

## <a name="other-controls-and-features"></a>Další ovládací prvky a funkce

V model Windows Forms existuje mnoho dalších funkcí, které umožňují rychle a snadno implementovat běžné úlohy, jako je podpora pro vytváření dialogových oken, tisk, přidání nápovědu a dokumentace a lokalizace aplikace do více jazyků. Kromě toho model Windows Forms spoléhá na robustní bezpečnostní systém .NET Framework, což vám umožní uvolnit zákazníkům více zabezpečených aplikací.

Podrobné informace o používání těchto funkcí najdete v následujících tématech nápovědy:

|Akce|Seznamte se s |
|--------|---------|
|Tisk obsahu formuláře|[Postupy: Tisk grafiky v modelu Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Další informace o model Windows Forms zabezpečení|[Přehled zabezpečení ve Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Přehled produktu Windows Forms](../../../framework/winforms/windows-forms-overview.md)
- [My.Forms – objekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
