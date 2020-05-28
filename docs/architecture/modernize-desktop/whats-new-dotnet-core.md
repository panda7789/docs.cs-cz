---
title: Co je nového u .NET Core for Desktop?
description: Přečtěte si o .NET Core, rozdílech mezi .NET Core a .NET Framework a novými přidanými funkcemi.
ms.date: 05/12/2020
ms.openlocfilehash: b4fc0cb2841fe13b000223aefc5eaf63bd911994
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144261"
---
# <a name="whats-new-with-net-core-for-desktop"></a>Co je nového u .NET Core for Desktop?

Počínaje rozhraním .NET Core 3,0 podporuje .NET Core model Windows Forms a WPF. Takže teď máte možnost volit mezi .NET Framework a .NET Core pro aplikace klasické pracovní plochy. Tato kapitola popisuje, co je .NET Core a jaké jsou jeho výhody pro desktopové aplikace.

## <a name="the-motivation-behind-net-core"></a>Motivace za .NET Core

Od jejího spuštění v 2002 se .NET Framework vyvinula spousta let, aby podporovala mnoho technologií, jako jsou model Windows Forms, ASP.NET, Entity Framework, Windows Store a spousta dalších. Všechna jsou v podstatě odlišná. Proto Microsoft se k tomuto vývoji přibližuje tím, že vezme části .NET Framework a vytvoří pro každou technologii jiný aplikační zásobník. Díky tomu můžou být možnosti vývoje přizpůsobené potřebám konkrétního zásobníku, což maximalizuje potenciál každé platformy. To má za následek fragmentaci ve verzích .NET Framework udržovaných různými nezávislými týmy. Všechny tyto zásobníky mají společnou strukturu, která obsahuje model aplikace, rozhraní a modul runtime, ale liší se v implementaci každé z těchto částí.

Pokud cílíte jenom na jednu z těchto platforem, můžete použít tento model. V mnoha případech ale můžete potřebovat více než jednu cílovou platformu ve stejném řešení. Vaše aplikace může mít například součást Správce stolního počítače, web směřující na zákazníka, který sdílí back-end logiku spuštěnou na serveru a dokonce i v mobilním klientovi. V takovém případě potřebujete jednotné prostředí pro kódování, které může zahrnovat všechny tyto svislé prvky .NET.

V době vydání systému Windows 8 byl koncept přenosných knihoven tříd (PCLs) zanesen. Původně .NET Framework byla navržena s předpokladem, že by byla vždy nasazena jako jediná jednotka [, takže ještě](https://wikipedia.org/wiki/Decomposition_(computer_science)) nedošlo k obavám. Chcete-li čelit problému sdílení kódu mezi svislými, je nutné, aby byla siloa v tom, jak refaktorovat rozhraní. Účelem smluv je poskytnout dobře vyladěnou plochu rozhraní API. Kontrakty jsou jednoduše sestavení, která kompilujete proti a jsou navržena s řádným faktoringem při pořizování závislostí mezi nimi.

To vede k rozhodnutí o rozdílech rozhraní API mezi svislými a na úrovni sestavení, a to na rozdíl od úrovně rozhraní API, kterou jsme předtím používali. Tento aspekt povolil prostředí knihovny tříd, které může být cíleno na více svislých, označované také jako přenositelné knihovny tříd.

![Historie verzí .NET Framework](./media/whats-new-dotnet-core/release-history.png)

S PCL je prostředí vývoje sjednocené ve svislých oblastech na základě tvaru rozhraní API. A co nejvíc stačí k vytváření knihoven běžících na různých svislých, jsou také řešeny. Je však Skvělé, že rozhraní API jsou přenosná pouze v případě, že je implementace přesunuta směrem nahoru ve všech svislých.

Lepším řešením je sjednocení implementací ve svislých verzích tím, že poskytuje správnou implementaci místo zobrazení ve správném měřítku. Je velice jednodušší položit každý tým, který vlastní určitou komponentu, aby se zamyslující nad tím, jak jejich rozhraní API fungují napříč všemi vertikály, než se snažíte úplně poskytnout konzistentní zásobník rozhraní API. Zde je místo, kde .NET Standard přichází. Další informace najdete v další části.

Další velká výzva musí dělat s tím, jak je .NET Framework nasazená. .NET Framework je architektura platná pro počítač. Všechny změny, které v něm probíhají, ovlivňují všechny aplikace, které na ní pobírají závislost. I když tento model nasazení má mnoho výhod, jako je například snížení místa na disku a centralizovaného přístupu ke službám, prezentuje některé nástrah.

Aby bylo možné začít používat, je obtížné vývojářům aplikací převzít závislost na nedávno vydaném rozhraní. Musí buď přebírat závislost na nejnovějším operačním systému, nebo poskytnout instalační program aplikace, který nainstaluje .NET Framework společně s aplikací. Pokud jste vývojář webu, možná tuto možnost nebudete mít i v případě, že IT oddělení stanoví verzi podporovanou serverem.

I v případě, že jste se ochotni předávat instalačnímu programu k řetězení .NET Framework instalačnímu programu, může se stát, že upgrade .NET Framework může přerušit jiné aplikace.

Navzdory úsilí o poskytování zpětně kompatibilní verze rozhraní jsou k dispozici kompatibilní změny, které mohou přerušit aplikace. Například přidání rozhraní k existujícímu typu může změnit způsob serializace tohoto typu a způsobit problémy v závislosti na existujícím kódu. Vzhledem k tomu, že je nainstalovaná základní platforma .NET Framework, boj proti těmto přerušením scénářům zpomaluje tempo inovací v rámci .NET Framework.

Pro vyřešení všech těchto problémů vyvinula společnost Microsoft .NET Core pro přístup k vývoji platformy .NET.

## <a name="introduction-to-net-core"></a>Úvod do .NET Core

.NET Core je vývoj technologie Microsoft .NET v modulárních, vysoce platforem, open source a připravené platformě pro Cloud. Spouští se v systémech Windows, macOS a Linux s plány, aby je bylo možné spustit také pro architektury založené na ARM, jako je Android a IoT.

Účelem .NET Core je poskytnout jednotnou platformu pro všechny typy aplikací, mezi které patří Windows, platforma a mobilní aplikace. [.NET Standard](../../standard/net-standard.md) to umožňuje poskytováním sdílených základních rozhraní API, které každý model aplikace potřebuje, a vyloučením rozhraní API specifického pro model aplikace.

Tato architektura poskytuje aplikacím mnoho výhod z pohledu efektivity a výkonu, což zjednodušuje balení a nasazení na různých podporovaných platformách.

Výhody .NET Core přicházejí z těchto tří charakteristik:

- **Pro různé platformy:** Umožňuje spuštění aplikace na různých platformách (Windows, macOS a Linux).
- **Open Source:** platforma .NET Core je open source a dostupná prostřednictvím GitHubu, která podporuje transparentnost a komunitní příspěvky.
- **Podporováno:** Společnost Microsoft oficiálně podporuje .NET Core.

Od .NET Core 3,0, kromě stávající podpory pro web i Cloud, je taky dostupná podpora pro domény desktopové, IoT a AI. Cílem této architektury je působivé: cílení na každý typ předstávajícího a budoucího vývojového prostředí .NET. Microsoft plánuje dokončit tuto vizi s .NET 5 na konci 2020. Název "Core" byl odebrán za účelem posílení jeho jedinečnosti v .NET World.

![Všechny domény rozhraní .NET 5](./media/whats-new-dotnet-core/all-domains-of-dotnet5.png)

## <a name="net-framework-vs-net-core"></a>.NET Framework vs. .NET Core

Takže teď, když jste se seznámili s relevancí .NET Core v rámci strategie Microsoft pro .NET, se můžete setkat s tím, co se stane s .NET Framework. Můžete se ptát na otázky, jako je například: Chcete ji opustit? Ztratí se? Jaké jsou moje možnosti, jak modernizovat aplikace, které mám na .NET Framework?

V 2019 byla vydána poslední verze **.NET Framework-4,8** . Zahrnuje tři hlavní vylepšení desktopových aplikací:

- **Moderní ovládací prvky prohlížeče a multimédií**: dnešní aplikace pro desktopové aplikace .NET používají k zobrazení HTML a přehrávání mediálních souborů Internet Explorer a Windows Media Player. Vzhledem k tomu, že tyto starší ovládací prvky nezobrazují nejnovější kód HTML nebo chtějí přehrát nejnovější mediální soubory, byly přidány nové ovládací prvky, které využívají výhody Microsoft Edge a novějších mediálních přehrávačů, které podporují nejnovější standardy.
- **Přístup k ovládacím prvkům UWP**: UWP obsahuje nové ovládací prvky, které využívají nejnovější funkce Windows a dotykové displeje. Pro použití těchto nových funkcí a ovládacích prvků nemusíte přepisovat své aplikace, takže můžete tyto nové funkce použít ve svém stávajícím WPF nebo model Windows Formsovém kódu.
- **Vylepšení s vysokým rozlišením DPI**: rozlišení displejů se zvyšuje na 4k a 8K rozlišení. Proto .NET Framework 4,8 přidává nová vylepšení HDPI, aby se zajistilo, že vaše stávající aplikace model Windows Forms a WPF budou vypadat skvěle na těchto nových displejích.

Vzhledem k tomu, že je instalace .NET Framework nainstalovaná na milionů počítačů, Microsoft je bude dál podporovat, ale nepřidá nové funkce.

.NET Core je open source verze .NET pro různé platformy a rychlé přesuny. Vzhledem k tomu, že se jedná o souběžnou povahu, může provádět změny bez obav z porušení jakékoli aplikace. To znamená, že .NET Core získá nová rozhraní API a funkce jazyka v čase, který .NET Framework ne. Kromě toho **rozhraní .NET Core** již obsahuje funkce, které nebyly pro .NET Framework možné, například:

- **Souběžné verze rozhraní .NET podporující model Windows Forms a WPF**: Tato akce řeší problém vedlejších účinků při aktualizaci verze Frameworku počítače. Na stejný počítač může být nainstalováno více verzí rozhraní .NET Core a každá aplikace určuje, kterou verzi rozhraní .NET Core má použít. Ještě víc, teď můžete vyvíjet a spouštět model Windows Forms a WPF nad .NET Core.
- **Vložení rozhraní .NET přímo do aplikace**: rozhraní .NET Core můžete nasadit jako součást balíčku aplikace. Díky tomu můžete využít výhod nejnovější verze, funkcí a rozhraní API, aniž byste museli čekat na instalaci konkrétní verze na počítač.
- Využijte **výhod funkcí .NET Core**: .NET Core je rychlé přesunutí open source verze .NET. Jeho souběžný typ umožňuje rychlé zavedení nových inovativních rozhraní API a vylepšení knihoven základních tříd (BCL) bez rizika přerušení kompatibility. Nyní model Windows Forms a aplikace WPF můžou využít výhod nejnovějších funkcí .NET Core, které také obsahují přísnější opravy pro výkon modulu runtime, podporu vysokého rozlišení a tak dále.

Důležitou součástí plánu Microsoftu bylo usnadnit vývojářům přesunout aplikace do .NET Core a v budoucnu do .NET 5. Pokud ale máte stávající aplikace .NET Framework, neměli byste mít vliv na přechod na .NET Core. .NET Framework bude plně podporovaná a bude vždycky součástí Windows. Pokud ale chcete, aby v budoucnu používaly nejnovější jazykové funkce a rozhraní API, bude nutné přesunout vaše aplikace do .NET Core.

Pro vaši značku – nové desktopové aplikace doporučujeme začít přímo na .NET Core. Je to odlehčená a více platforem, pracuje souběžně, má vysoký výkon a je naprosto přesně v kontejnerech a architekturách mikroslužeb.

![Můžete aktualizovat .NET Framework aplikace pomocí nejnovější .NET Framework verze nebo portovat aplikace na .NET Core.](./media/whats-new-dotnet-core/framework-vs-core.png)

## <a name="net-standard-vs-pcl"></a>.NET Standard vs. PCL

[.NET Standard](../../standard/net-standard.md) je formální specifikace rozhraní API .NET, která jsou určená k dispozici pro všechny implementace .NET. Motivace za .NET Standard vytváří větší jednotnost v ekosystému .NET. .NET Standard je specifikace rozhraní .NET API, které tvoří jednotnou sadu kontraktů pro zkompilování kódu. Tyto smlouvy jsou implementované v každém charakteru .NET, což umožňuje přenositelnost napříč různými implementacemi .NET.

.NET Standard umožňuje následující klíčové scénáře:

- Definuje jednotnou sadu rozhraní API knihoven základních tříd pro všechny implementace .NET, které mají být implementovány nezávisle na zatížení.
- Umožňuje vývojářům vytvářet přenosné knihovny, které jsou použitelné napříč implementacemi rozhraní .NET, a to pomocí stejné sady rozhraní API.

.NET Standard je vývoj PCLs a v následujícím seznamu jsou uvedeny základní rozdíly mezi .NET Standard a PCLs:

- .NET Standard je sada spravovaných rozhraní API vydaných společností Microsoft. PCLs nejsou.
- Rozhraní API, která obsahuje PCL, jsou závislá na platformách, na které se rozhodnete při jejich vytváření cílit. Tato možnost vytvoří pouze PCL pro konkrétní cíle, které zvolíte.
- .NET Standard je platforma nezávislá, může běžet kdekoli, v systémech Windows, macOS, Linux atd.
- PCLs může také běžet na více platforem, ale má více omezeného dosahu. PCLs může cílit jenom na omezené sady platforem.

## <a name="new-desktop-features-in-net-core"></a>Nové funkce plochy v .NET Core

### <a name="support-for-windows-forms-and-wpf"></a>Podpora pro model Windows Forms a WPF

Model Windows Forms a WPF jsou součástí .NET Core od verze 3,0. Obě prezentační rozhraní jsou jenom pro Windows, takže se nepoužívají pro různé platformy. WPF můžete představit jako bohatou vrstvu přes rozhraní DirectX a model Windows Forms jako užší vrstvu nad rozhraním GDI+. WPF a model Windows Forms v systému Windows skvělou úlohu vystavovat a vykonávat většinu funkcí desktopové aplikace. Takže model Windows Forms a WPF jsou k dispozici pro .NET Core a .NET Framework. Teď můžete začít své nové desktopové aplikace zaměřené na .NET Core a migrovat svoje stávající z .NET Framework do .NET Core.

Nová verze .NET Standard verze 2,1 byla vydána ve stejnou dobu jako rozhraní .NET Core 3,0. Podle očekávání podporují verze .NET Core 3. x .NET Standard 2,1 a starší verze.

Je také důležité si všimnout, že implementace model Windows Forms a WPF pro .NET Core jsou open source.

### <a name="xaml-islands"></a>XAML – ostrovy

[XAML – ostrovy](/windows/apps/desktop/modernize/xaml-islands) je sada komponent pro vývojáře, aby používala nové ovládací prvky Windows 10 (ovládací prvky UWP v jazyce XAML) ve svých současných aplikacích WPF, model Windows Forms a nativních aplikacích Win32 (jako je MFC). Můžete mít své "ostrovy" ovládacích prvků XAML pro UWP všude, kde chcete v aplikacích Win32.

Tyto ostrovy XAML jsou možné, protože Windows 10 verze 1903 zavádí sadu rozhraní API, která umožňuje hostování obsahu UWP ve Windows v systému Win32 pomocí obslužných rutin Windows (HWnd). Všimněte si, že na ostrovech XAML můžou používat jenom aplikace běžící ve Windows 10 1903 a novějších.

Aby bylo snazší vytvářet na ostrovech XAML pro vývojáře model Windows Forms a WPF, zavádí sada nástrojů Windows Community Toolkit sadu obálk .NET v několika balíčcích NuGet. Tyto obálky jsou zabalenými a hostujícími ovládacími prvky:

- Zabalené ovládací prvky [WebView](/windows/communitytoolkit/controls/wpf-winforms/webview), [WebViewCompatible](/windows/communitytoolkit/controls/wpf-winforms/webviewcompatible), [InkCanvas](/windows/communitytoolkit/controls/wpf-winforms/inkcanvas), [MediaPlayerElement](/windows/communitytoolkit/controls/wpf-winforms/mediaplayerelement)a [MapControl](/windows/communitytoolkit/controls/wpf-winforms/mapcontrol) zabalí některé ovládací prvky pro UWP v jazyce XAML do ovládacích prvků model Windows Forms nebo WPF, které těmto vývojářům skrývají koncepty UWP.
- Ovládací prvek [WindowsXamlHost](/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) pro model Windows Forms a WPF povoluje jiné nezabalené ovládací prvky XAML a vlastní ovládací prvky lze načíst do ostrova XAML.

### <a name="access-to-all-windows-10-apis"></a>Přístup ke všem rozhraním API Windows 10

Windows 10 má skvělé množství rozhraní API, které můžou vývojáři pracovat s nástrojem. Tato rozhraní API poskytují přístup k nejrůznějším funkcím, jako je ověřování, Bluetooth, schůzky a kontakty. Tato rozhraní API se teď zveřejňují prostřednictvím .NET Core a vývojářům v systému Windows umožňuje vytvářet výkonné desktopové aplikace s využitím možností přítomných ve Windows 10.

### <a name="side-by-side-support-and-self-contained-exes"></a>Souběžná podpora a samostatně zahrnutá exe

Model nasazení .NET Core je jedním z největších výhod, které budou vývojáři pro desktopové prostředí systému Windows používat s .NET Core. Možnost globálně nainstalovat .NET Core poskytuje velkou z výhod, které jsou součástí .NET Framework, a přitom přináší výhody pro hlavní instalaci a údržbu, a to bez nutnosti místní aktualizace.

Po vydání nové verze .NET Core můžete každou aplikaci na počítači aktualizovat podle potřeby, aniž by to mělo vliv na ostatní aplikace. Nové verze rozhraní .NET Core jsou nainstalovány ve vlastních adresářích a existují "vedle sebe".

Pokud potřebujete nasadit s izolací, můžete s aplikací nasadit .NET Core. .NET Core nasadí vaši aplikaci s modulem runtime .NET Core jako v jednom spustitelném souboru.

Tyto možnosti nasazení byly od vývojářů vyžádány poměrně dlouhou dobu, ale byly obtížné dosáhnout použití .NET Framework. Modulární architektura, kterou používá .NET Core, zajišťuje tyto možnosti flexibilního nasazení.

### <a name="performance"></a>Výkon

Vzhledem k tomu, že jeho začátek, cílící na webové a cloudové úlohy, měl .NET Core výkon připojený ke svému DNA. Kód na straně serveru musí být dostatečně výkonný pro splnění scénářů s vysokou mírou souběžnosti a skóre .NET Core v současnosti jako nejlepší výkonná webová platforma na trhu.

Můžete využít výhod těchto vylepšení výkonu při vytváření nové generace aplikací klasické pracovní plochy pomocí .NET Core.

## <a name="benefits-of-open-source"></a>Výhody Open Source

Jenom několik slov o typu open source v .NET Core. Sestavování zásobníku pro různé platformy je složité, které vyžaduje interakci specializovaných týmů na každé z cílových platforem. Toto úsilí potřebuje mnohem spolupracovat zevnitř Microsoftu i mimo něj. Díky tomu, že se stane otevřeným zdrojem, který se tak otevře pro veřejnou spolupráci, získáte na místě konečný styl agilního vývoje a získáte tak přehled o kvalitě od velkých a aktivních komunit vývojářů.

Toto je klíč úspěšnosti .NET Core, který bude nadále urychlení výše zmíněného plánu: bude jedinou platformou .NET, kterou bude moci nějaký vývojář někdy potřebovat k sestavení jakékoli aplikace.

>[!div class="step-by-step"]
>[Předchozí](why-modern-applications.md) 
> [Další](migrate-modern-applications.md)
