---
title: Proč moderní desktopové aplikace
description: Přečtěte si o technologiích pro stolní počítače, jako jsou model Windows Forms, WPF a UWP, v moderním světě.
ms.date: 09/16/2019
ms.openlocfilehash: f8b70ba9e0ee97a6e0938e3219ecd0d2324248ae
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423276"
---
# <a name="why-modern-desktop-applications"></a>Proč moderní desktopové aplikace

## <a name="introduction"></a>Úvod

### <a name="a-story-of-one-company"></a>Příběh jedné společnosti

Zpět v rané 2000s jedna nadnárodní společnost zahájila vývoj řešení distribuované plochy pro výměnu informací mezi různými pobočkami společnosti a provádění optimalizovaných operací u centralizovaných jednotek. Zvolili jsme novou architekturu nazvanou model Windows Forms (označuje se také jako WinForms) pro vývoj aplikací. V průběhu let se projekt vyvíjel do vyspělé, dobře testované a včas prověřené aplikace se stovkami tisíc řádků kódu. Uplynulý čas a .NET Framework 2,0 již není horkou novou technologií. Vývojáři, kteří pracují na této aplikaci, čelí dilematem. Chtějí využívat nejnovější sadu technologií ve svém vývoji a mít jejich vzhled a atmosféru. Současně si nepřeje, abyste si vyvolali skvělý produkt, který sestavil více než 15 let, a přepsat celou aplikaci úplně od začátku.

### <a name="your-story"></a>Váš příběh

Můžete se setkat ve stejném člunu, kde máte vyspělé aplikace model Windows Forms nebo Windows Presentation Foundation (WPF), u kterých proukázala jejich spolehlivost během let. Tyto aplikace pravděpodobně budete chtít dál používat po řadu dalších let. Ve stejnou chvíli, vzhledem k tomu, že tyto aplikace byly zapsány před nějakou dobou, můžou chybět možnosti, jako je moderní vzhled, výkon, integrace s novými zařízeními a funkcemi platformy, a tak dále, což jim dává dojem "Star tech". K dispozici je další problém, který by vás mohl týkat vývojářů. Při práci na starších verzích .NET Framework a při údržbě aplikací, které byly zapsány, se můžete setkat s tím, že se vám nenaučíte vytvářet nové technologie a nemůžete k tvorbě moderních technických dovedností chybět. Pokud je to váš příběh – tato kniha je určena pro vás.

## <a name="desktop-applications-nowadays"></a>Desktopové aplikace současné době

Před zvýšením počtu internetových aplikací byly desktopové aplikace hlavním přístupem k vytváření softwarových systémů. Vývojáři mohou zvolit libovolný programovací jazyk, například COBOL, FORTRAN, VB6 nebo C++. Ale tam, kde byly vyvinuty malé nástroje nebo komplexní distribuované architektury, byly všechny desktopové aplikace.

Technologie sítě Internet pak začaly nasazovat vývojovou síť a získala více a více techniků, a to s výhodami, jako je snadné nasazení a zjednodušené distribuční procesy. Skutečnost, že po nasazení webové aplikace do produkčního prostředí mají všichni uživatelé i automatické aktualizace, mají velký dopad na flexibilitu softwaru.

Internetová infrastruktura, základní protokoly a standardy jako HTTP a HTML nejsou navržené pro vytváření složitých aplikací. V důsledku toho bylo hlavním úsilím vývoje zpět v rámci jednoho cíle: k tomu, aby webové aplikace měly stejné možnosti jako aplikace pro stolní počítače, jako je například rychlé zadání dat a Správa stavu.

I když se webové a mobilní aplikace pěstují s nezpracovaným tempem, pro určité úlohy aplikace klasické pracovní plochy stále drží číslo na jednom místě z pohledu efektivity a výkonu. Vysvětluje, proč existují miliony vývojářů, kteří sestavují své projekty pomocí WPF a WinForms a množství těchto aplikací neustále roste.

Zde jsou některé důvody pro výběr aplikací klasické pracovní plochy ve vašem vývojovém prostředí:

- Aplikace klasické pracovní plochy mají lepší interakci s počítačem uživatele.
- Výkon aplikací klasické pracovní plochy pro složité výpočty je mnohem vyšší než výkon webových aplikací.
- Spuštění vlastní logiky na straně klienta je možné, ale mnohem obtížnější pomocí webové aplikace.
- Použití multithreadingu je v desktopové aplikaci jednodušší a efektivnější.
- Výuková křivka pro navrhování uživatelských rozhraní (uživatelská rozhraní) není strmé. A pro WinForms je zcela intuitivní s možností přetažení návrháře model Windows Forms.
- Je snadné začít vytvářet kódování a testovat algoritmy bez nutnosti nastavovat serverovou infrastrukturu nebo se starat o problémy s připojením, brány firewall a kompatibilitu prohlížečů.
- Ladění je ve srovnání s laděním webu výkonné.
- Přístup k hardwarovým zařízením, jako jsou kamery, Bluetooth nebo čtecí zařízení karet, je snadné.
- Vzhledem k tomu, že tato technologie byla v době delší, je pro vývoj aplikací klasické pracovní plochy k dispozici mnoho odborníků a znalostní báze.

Jak můžete vidět, vývoj pro Desktop je skvělý z mnoha důvodů. Tato technologie je vyspělá a časově testována, vývojový cyklus je rychlý, ladění je výkonné a pravděpodobně, aplikace klasické pracovní plochy mají méně složité a jednodušší začít s.

Společnost Microsoft nabídla mnoho technologií desktopového prostředí v průběhu let od Win32 zavedených v 1995 až Univerzální platforma Windows (UWP) vydané v 2016.

![Desktopové technologie společnosti Microsoft](./media/why-modern-applications/microsoft-desktop-technologies.png)

Na základě průzkumu publikovaného službou Telerik od dubna 2016 jsou nejoblíbenější technologie pro vytváření desktopových aplikací pro Windows model Windows Forms, WPF a UWP.

![Telerik průzkum ukazující model Windows Forms, WPF a UWP jako nejoblíbenější technologie pro stolní počítače](./media/why-modern-applications/telerik-survey.png)

Můžete vyvíjet v libovolném z nich pomocí C# a Visual Basic, ale podívejme se, jak se to podíváme.

### <a name="windows-forms"></a>Windows Forms

Vydaná v 2002 model Windows Forms je spravované rozhraní a je nejstarší, nejčastěji používaná technologie pro stolní počítače postavená na modulu Windows Graphics Device Interface (GDI). Nabízí hladké možnosti přetahování při vývoji uživatelských rozhraní v aplikaci Visual Studio.  Současně model Windows Forms spoléhá na Visual Studio designer jako na hlavní způsob vývoje uživatelského rozhraní, takže vytváření vizuálních komponent z kódu není triviální.

Následující seznam shrnuje hlavní vlastnosti model Windows Forms:

- Vyspělá technologie s velkým množstvím ukázek kódu a dokumentace.
- Výkonný a produktivní Návrhář. Nemusíte proto pohodlně navrhovat uživatelské rozhraní z kódu.
- Snadná a intuitivní, jak se naučit, díky prostředí přetažení návrháře.
- Podporováno u libovolné verze systému Windows.
- Podporováno v rozhraní .NET Core 3,0 a novějších verzích.

### <a name="wpf"></a>WPF

V závislosti na specifikaci jazyka XAML, WPF upřednostňuje jasné oddělení mezi uživatelským rozhraním a kódem. XAML nabízí takové možnosti, jako je šablonování, stylování a vazba, které jsou vhodné pro vytváření rozsáhlých aplikací. Podobně jako model Windows Forms se jedná o spravované rozhraní, ale návrh je modulární a opakovaně použitelný.

Tady jsou hlavní funkce WPF:

- Vyspělá technologie.
- Návrhář je k dispozici, ale vývojáři obvykle dávají přednost vytváření návrhu z kódu pomocí deklarativního XAML.
- Výuková křivka je steeper než model Windows Forms.
- Podporováno u libovolné verze systému Windows.
- Podporováno v rozhraní .NET Core 3,0 a novějších verzích.

### <a name="uwp"></a>UPW

UWP nepoužívá jenom prezentační architekturu, jako je WPF a model Windows Forms, ale je to také samotná platforma. Tato platforma má:

- Vlastní sada rozhraní API (rozhraní prostředí Windows Runtime API).
- Nový systém nasazení (MSIX)
- Moderní model životního cyklu aplikací (pro nízké využití baterie).
- Nový systém správy prostředků (založený na souborech PRI).

Platforma se vytvořila tak, aby podporovala všechny druhy vstupních systémů (jako jsou rukopis, dotykové ovládání, gamepad, myš, klávesnice, pohledu atd.), a to ve všech formách, které se týkají výkonu a nízké spotřeby baterie. Z těchto důvodů používá prostředí Windows 10 OS části platformy UWP.

![Struktura UWP](./media/why-modern-applications/uwp-structure.png)

UWP obsahuje prezentační rozhraní, které je založené na jazyce XAML, jako je WPF, ale má několik důležitých rozdílů, například:

- Aplikace se spouštějí v kontejnerech aplikací. Kontejnery aplikací určují, k jakým prostředkům má aplikace pro UWP přístup.
- Podporováno pouze ve Windows 10.
- Aplikace se dají nasadit pomocí Microsoft Store pro snazší nasazení.
- Navrženo jako součást rozhraní prostředí Windows Runtime API.
- Obsahuje rozsáhlou sadu propracovaných vestavěných ovládacích prvků a další ovládací prvky, které jsou k dispozici prostřednictvím balíčků NuGet knihovny uživatelského rozhraní Microsoft (WinUI Library), aktualizované každé několik měsíců.

## <a name="a-tale-of-two-platforms"></a>Sdělovač dvou platforem

Za posledních 20 let byly při zvětšování technologií uživatelského rozhraní a za základě cesty od model Windows Forms do UWP také vyvíjeny hardwarové jednotky s malým množstvím CRT monitorované monitory s vysokým ROZLIŠENÍm a odlehčenými tablety a telefony s různými technikami vstupních dat, jako jsou dotyková a inkoustová. Výsledkem těchto změn je vytvoření dvou různých konceptů: desktopová aplikace a moderní aplikace. Moderní aplikace je ta, která zohledňuje různé faktory formuláře zařízení, různé vstupní a výstupní metody a využívá moderní funkce plochy při spuštění v modelu spouštění v izolovaném prostoru. (Tradiční) desktopová aplikace je na druhé straně aplikace, která potřebuje plné uživatelské rozhraní s vysokou hustotou ovládacích prvků, která je nejlépe ovládaná myší a klávesnicí.

Následující tabulka popisuje rozdíly mezi těmito dvěma koncepty:

|   | Moderní aplikace | Desktopová aplikace |
| --- | --- | --- |
| Zabezpečení | Obsahovalo se &amp; skvělé základy. Navrženo od základu pro zajištění ochrany osobních údajů uživatele, správy výdrže baterie a zaměření na zabezpečení zařízení.  | &amp;Úroveň zabezpečení správce uživatele Máte nativní přístup ke složkám registru a pevného disku. |
| Nasazení | Instalace a aktualizace jsou spravovány platformou.   | MSI, vlastní instalační programy &amp; aktualizace. Tradičně je zdrojem souvisejícím problémům správou pro vývojáře a IT manažery.  |
| Distribuce | Balíčky podepsané pro důvěryhodné distribuce &amp; Distribuce je prováděna z důvěryhodného zdroje a nikdy z webu.  | Web, &amp; vlastní distribuce SCCM. Bez kontroly nad tím, co je nainstalováno, má vliv na celý počítač.   |
| Uživatelské rozhraní | Moderní uživatelské rozhraní. Různé vstupní mechanismy, rukopis, dotykové ovládání, gamepad, klávesnice, myš atd.  | Model Windows Forms, WPF, MFC. Navržený pro myš a klávesnici pro zhuštěné uživatelské rozhraní a pro zajištění nejvyšší produktivity z plochy.  |
| Data | První cloudová data s přehledy Zdroj pravdy v cloudu Přehledy o tom, co se stane s vaší aplikací a jak se to dělá  | Místní data. Tradiční aplikace klasické pracovní plochy obvykle potřebují některá místní data.  |
| Návrh | Navrženo pro opakované použití. Přihlaste se na různých platformách, front-endu a back-end a spusťte assety na mnoha místech, jak je to možné.  | Určeno jenom pro stolní počítače se systémem Windows  |

Jako součást závazku poskytovat vývojářům nejlepší nástroje pro sestavování aplikací, společnost Microsoft přináší skvělé úsilí, aby tyto koncepce přineslo, nebo můžeme dokonce vydávat i platformy, abychom vývojářům zajistili nejlepší z obou světů. V důsledku toho společnost Microsoft provedla obousměrné úsilí mezi oběma platformami.

![Obousměrné úsilí mezi moderní aplikací a desktopové aplikace](./media/why-modern-applications/bidirectional-effort.png)

1. Přesuňte scénáře aplikace pro stolní počítače do moderní aplikační platformy. Tradiční vývoj desktopových aplikací je stále oblíbený, protože řeší určité scénáře dobře. Je vhodné provést tyto běžné scénáře pro stolní počítače a přenést je do moderní platformy pro stolní počítače, aby bylo možné plně podporovat platformu.

    ![Přesun scénářů aplikací pro stolní počítače do moderní aplikační platformy](./media/why-modern-applications/desktop-to-modern.png)

1. Přesuňte moderní funkce aplikace do aplikací klasické pracovní plochy. Pro existující desktopové aplikace, které potřebují využít možnost využívat moderní možnosti bez nutnosti přepisovat od začátku, se funkce z moderní aplikační platformy vloží do aplikace klasické pracovní plochy.

    ![Přesun funkcí moderní aplikace do aplikací klasické pracovní plochy](./media/why-modern-applications/modern-to-desktop.png)

V této knize se zaměříme na druhou část a ukážeme, jak můžete modernizovat své stávající desktopové aplikace.

## <a name="paths-to-modernization"></a>Cesty k modernizaci

Struktura tohoto průvodce odráží tři různé osy k dosažení modernizace: moderní funkce, nasazení a instalace.

### <a name="modern-features"></a>Moderní funkce

Řekněme, že máte pracovní model Windows Forms aplikaci, kterou prodejní zástupce vaší společnosti používá k vyplnění objednávky zákazníka. V systému se objeví nový požadavek, který zákazníkovi umožní podepsat objednávku pomocí tabletového pera. Inkrál je nativní v dnešních operačních systémech a technologiích, ale během vývoje aplikace není dostupný.

V této cestě se dozvíte, jak můžete využít moderní funkce plochy pro vývoj stávajících desktopů.

### <a name="deployment"></a>Nasazení

Moderní vývojové cykly se nasadily, aby se zajistila flexibilita toho, jak se nové verze aplikací nasazují na každého jednotlivého uživatele. Vzhledem k tomu, že aplikace model Windows Forms a WPF jsou založené na konkrétní verzi .NET Framework, která musí být v počítači přítomna, nemůžou využít nové funkce verze .NET Framework bez zásahu uživatele, který má vliv na vedlejší účinky pro jiné aplikace běžící na stejném počítači. Má omezené inovační postup, který vývojářům nutí, aby si udrželi zastaralou verzi .NET Framework.

Vzhledem k tomu, že se spouští .NET Core 3,0, můžete využít nový přístup k nasazení více verzí .NET Core souběžně a určit, která verze .NET Core má každá aplikace cílit. Tímto způsobem můžete použít nejnovější funkce v jedné aplikaci a přitom si je jisti, že nebudete přerušovat žádné jiné aplikace.

### <a name="installation"></a>Instalace

Aplikace klasické pracovní plochy vždy spoléhají na určitý proces instalace předtím, než ho uživatel může začít používat. Tato skutečnost se zavedla do hry a sady technologií, z MSI a ClickOnce na vlastní instalační programy nebo dokonce na nasazení XCOPY. Každá z těchto metod se zabývá problémy s jemná, protože aplikace potřebují způsob přístupu ke sdíleným prostředkům v počítači. Někdy instalace potřebuje přístup k registru, aby mohl vkládat nebo aktualizovat nové hodnoty klíčů, někdy aktualizovat sdílené knihovny DLL, na které odkazuje hlavní aplikace. To způsobuje nepřetržité starostíí pro uživatele, což znamená, že po instalaci některé aplikace nebude počítač nikdy stejný, ani když ho odinstalujete později.

V této knize zavádíme nový způsob, jak nainstalovat aplikace s MSIX, které řeší problém popsaný výše. Naučíte se, jak můžete pro svou aplikaci snadno nastavit balení, instalaci a aktualizace.

>[!div class="step-by-step"]
>[Předchozí](index.md) 
> [Další](whats-new-dotnet-core.md)
