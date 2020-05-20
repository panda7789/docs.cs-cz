---
title: Nasazení moderních desktopových aplikací
description: Vše, co potřebujete znát o nasazování moderních aplikací klasické pracovní plochy.
ms.date: 05/12/2020
ms.openlocfilehash: 4a4d93caf1c2f8f58d48ee3199bbe6983fa939f4
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423255"
---
# <a name="deploying-modern-desktop-applications"></a>Nasazení moderních desktopových aplikací

Když vyvíjíte desktopové aplikace, jedna z věcí, kterou je potřeba zvážit, je, jak bude vaše aplikace zabalená a nasazená do počítačů uživatelů. Problém s balíčkem, nasazením a instalací je, že obvykle spadá do kostar IT specialistů, kteří se zabývají i různými akcemi než vývojáři.

Tyto dny jsme obeznámeni s konceptem DevOps, kde vývojáři a IT specialisté úzce spolupracují na přesunu aplikací do jejich produkčních prostředí. Ale pokud jste se přihlásili z plochy na více než 10 let, možná jste viděli následující text. Tým vývojářů spolupracuje na plnění konečných termínů projektu. Obchodní lidé jsou nervové, protože potřebují systém pracovat na mnoha počítačích uživatelů pro spuštění společnosti. V "D-Day" vedoucí projektu kontroluje každý vývojář, že jejich kód funguje dobře a že vše je dobré, takže se dají dodávat. Tým balíčku pak zaznamená, že generuje nastavení pro aplikaci, distribuuje ho do všech uživatelských počítačů a sadu testovacích uživatelů spustí aplikaci. Také se pokoušejí, protože před zobrazením uživatelského rozhraní aplikace vyvolá výjimku, která říká "metoda ~ objektu ~ selhala". Nenouzové zahájení toku prostřednictvím vzduchu a krátkého šetření vede na mladého a už vás unavujeho vývojáře, který představil ovládací prvek třetí strany, který určitě pracoval na vývojovém počítači.

Instalace desktopových aplikací se tradičně Nightmare ze dvou hlavních důvodů:

- Nedostatečná jazyková verze spolupráce mezi vývojem a IT týmy.
- Nedostatku plného balení a nasazení technologie, kterou můžeme sestavit.

Ve skutečnosti jsme s fakty nepracovali, že v některých případech jste zavedli instalaci aplikace z těchto důvodů:

- Končí na vašem počítači některé nežádoucí vedlejší účinky.
- Některé aplikace, které byly dříve nainstalovány, přestaly fungovat.

Kromě toho nemůžete obnovit původní stav systému tím, že aplikaci odinstalujete. Používáme se k živému provozu této situace, kterou jsme mince jako "DLL Hell" nebo "Winrot".

V této kapitole budeme mluvit o MSIX. MSIX je zcela nová technologie od Microsoftu, která se snaží zachytit nejlepší z předchozích technologií, aby poskytovala pevný základ pro technologii balení v budoucnosti.

Co je potřeba pro balící technologii s modernizací? V takovém případě se zavede k tomu, že balení je zásadní pro podnik IT, který tam investovala i spousta peněz. Modernizace nesouvisí jenom s používáním nejnovějších technologií. Je také v souvislosti se zkrácením doby uvedení na trh od okamžiku definování podnikového požadavku, dokud vaše společnost nedodá klientovi funkci.

## <a name="the-modern-application-lifecycle"></a>Životní cyklus moderní aplikace

Dnes vývojáři napíší a sestavují kód pro aplikaci a pak předají vygenerované prostředky pro odborníky v oblasti IT. IT specialisté pak znovu nakonfigurují aplikaci a znovu zabalí, obvykle v MSI nebo novějším ve formátu balíčku sady App-V. Aplikace se pak nasadí pomocí různých kanálů a nástrojů. Jedním z hlavních problémů s tímto přístupem se běžně říká "balení paralysis". Problémem je to, že se tento cyklus opakuje pokaždé, když se aktualizuje aktualizace aplikace nebo aktualizace operačního systému.

Můžete vidět, jak se proces projeví na následujícím obrázku:

![Diagram znázorňující moderní životní cyklus IT](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

Společnosti potřebují způsob, jak rozdělit tento cyklus balení na tři nezávislé cykly:

- Aktualizace operačního systému
- Aktualizace aplikace
- Přizpůsobení

![Diagram znázorňující moderní cyklus IT virtuous](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

Předchozí diagram ukazuje, že můžete:

- Aktualizujte základní operační systém, aniž byste museli znovu zabalit své aplikace.
- Povolte z něho vlastní nastavení, aniž byste museli znovu zabalit původní balíček pro vývojáře.

Tato odmocnina vede k novému a modernímu životnímu cyklu IT, jak je znázorněno na následujícím obrázku:

![Diagram znázorňující životní cyklus aplikace pomocí nástrojů Microsoftu](./media/deploy-modern-applications/microsoft-it-tools.png)

Vývojáři vytvoří aplikaci a vygenerují balíček MSIX, který IT specialisté můžou spotřebovat a konfigurovat bez nutnosti opětovného balení. Společně s technologií MSIX společnost Microsoft vytvořila nástroje, které jim umožňují přizpůsobit a konfigurovat balíčky bez nutnosti opětovného balení.

## <a name="msix-the-next-generation-of-deployment"></a>MSIX: příští generace nasazení

Před MSIX bylo k dispozici několik technologií balení, jako jsou průvodci nastavením, MSI, ClickOnce, App-V a skriptování. Každá z těchto technologií má své vlastní síly a Microsoft se rozhodl vybrat nejlepší z nich pro sestavení MSIX. MSIX je postaven na základech těchto stávajících technologií, které vycházejí z každého z nich:

- App-V = \> containering
- ClickOnce = \> Automatické aktualizace
- MSI = \> snadné rozmístění

S MSIX získáte jednu technologii instalačního programu se všemi těmito funkcemi.

![Diagram znázorňující různé technologie, které měly vliv na sestavování MSIX](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a>Výhody MSIX

#### <a name="never-regret-installing-an-app"></a>Nikdy Nelitujte s instalací aplikace

MSIX poskytuje předvídatelné, spolehlivé a bezpečné nasazení. Deklarativní metoda obsažená v manifestu balíčku umožňuje operačnímu systému sledovat každý prostředek, který vaše aplikace potřebuje. Poskytuje také skutečnou čistou odinstalaci bez vedlejších účinků.

#### <a name="disk-space-optimization"></a>Optimalizace místa na disku

MSIX je optimalizovaná tak, aby snižovala nároky na místo na disku počítače uživatele. Vytvoří úložiště souborů s jednou instancí. To znamená, že pokud máte dva různé balíčky se stejnou knihovnou DLL, knihovna DLL není nainstalována dvakrát. Platforma se tento problém postará, protože ví, že všechny soubory, na které konkrétní aplikace nainstalovaná, nezpůsobí jeho deklarativní povahy. Také umožňuje mít různé verze knihovny DLL pracující vedle sebe.

Díky použití balíčků prostředků můžete snadno vytvářet vícejazyčné aplikace a operační systém se stará o instalaci těch, které se používají.

#### <a name="network-optimization"></a>Optimalizace sítě

MSIX detekuje rozdíly souborů na úrovni bloku bajtů, které umožňují funkci s názvem rozdílové aktualizace. To znamená, že při aktualizacích aplikace byly staženy pouze aktualizované bloky bajtů.

![Diagram, který ukazuje, jak MSIX spravuje rozdílové aktualizace](./media/deploy-modern-applications/msix-managing-updates.png)

Při instalaci streamování může uživatel rychle začít pracovat na vaší aplikaci, zatímco ostatní části aplikace se stáhnou na pozadí. Tato funkce přispívá k poutavému prostředí pro vaše uživatele.

Díky funkci volitelné balíčky budete v nasazení aplikace zacílit komponenty, takže je můžete v případě potřeby stáhnout.

#### <a name="simple-packaging-and-deployment"></a>Jednoduché balení a nasazení

AppManifest deklaruje správu verzí, cílení na zařízení a identifikuje standardní způsob pro každou aplikaci. Poskytuje také způsob, jak podepisovat prostředky, které poskytují základní bezpečnostní základ.

#### <a name="os-managed"></a>Spravované operačním systémem

Operační systém zpracovává všechny procesy pro instalaci, aktualizaci a odebrání aplikace. Aplikace se instalují na uživatele, ale stáhnou se jenom jednou a minimalizují se nároky na disk. Microsoft pracuje na poskytování MSIXho prostředí v systému Windows 7.

#### <a name="windows-provides-integrity-for-the-app"></a>Systém Windows poskytuje integritu pro aplikaci.

Pomocí digitálních podpisů můžete zaručit, že nenainstalujete aplikaci z nedůvěryhodných zdrojů. MSIX také brání manipulaci, protože:

- Udržuje záznam hodnot hash souborů.
- Zjistí, zda byl soubor změněn po instalaci.

#### <a name="works-for-the-entire-app-catalog"></a>Funguje pro celý katalog aplikací.

Jednou z zajímavých věcí o MSIX je to, že funguje pro celý katalog aplikací, model Windows Forms, WPF, MFC/ATL, Delphi, a to i v případě, že chcete provést nasazení xCopy, ClickOnce nebo předávat do úložiště, můžete použít stejný balíček MSIX.

### <a name="tools"></a>nástroje

#### <a name="windows-application-packaging-project"></a>Projekt Windows Application Packaging

K vygenerování balíčku pro desktopovou aplikaci můžete použít projekt projekt **balení aplikace systému Windows**   v aplikaci Visual Studio. Pak můžete tento balíček publikovat do Microsoft Store nebo ho bokem na jeden nebo více počítačů.

#### <a name="msix-packaging-tool"></a>Nástroj pro balení MSIX

Nástroj pro sbalení MSIX umožňuje znovu zabalit stávající aplikace Win32 do formátu MSIX. Nabízí interaktivní uživatelské rozhraní a příkazový řádek pro převody a poskytuje možnost převést aplikaci bez zdrojového kódu.

![Nástroj pro balení MSIX](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a>Rámec podpory balíčku

Rámec podpory balíčku je open-source sada, která vám pomůže použít opravy pro vaši stávající aplikaci Win32, pokud nemáte přístup ke zdrojovému kódu, aby ho bylo možné spustit v kontejneru MSIX. Rozhraní podpory balíčků pomáhá vaší aplikaci dodržovat osvědčené postupy pro moderní běhové prostředí.

#### <a name="app-installer"></a>Instalační program aplikace

Instalační program aplikace umožňuje instalaci aplikací pro Windows 10 dvojitým kliknutím na balíček aplikace. To znamená, že uživatelé nepotřebují k nasazování aplikací pro Windows 10 používat PowerShell ani jiné vývojářské nástroje. Instalační program aplikace může také nainstalovat aplikaci z webu, volitelné balíčky a související sady.

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a>Postup vytvoření balíčku MSIX z existující aplikace klasické pracovní plochy v systému Win32

Pojďme si projít procesem vytvoření balíčku MSIX z existující aplikace Win32. V tomto příkladu použijeme aplikaci model Windows Forms.

Chcete-li začít, přidejte do řešení nový projekt, vyberte projekt balíčku aplikace systému Windows a pojmenujte ho.

![Přidání nového projektu pro balení aplikace pro systém Windows](./media/deploy-modern-applications/add-packaging-project.png)

Uvidíte strukturu projektu balení a poznamenejte si speciální složku s názvem *aplikace*. V této složce můžete určit, které aplikace chcete zahrnout do balíčku. Může to být více než jeden.

![Struktura balícího projektu](./media/deploy-modern-applications/packaging-project.png)

Klikněte pravým tlačítkem na složku *aplikace* a vyberte projekt model Windows Forms, který chcete zabalit z řešení sady Visual Studio.

![Přidání projektu model Windows Forms do balícího projektu](./media/deploy-modern-applications/add-winforms-project.png)

V tuto chvíli můžete balíček zkompilovat a vygenerovat, ale podívejme se na několik věcí. Aby bylo možné zajistit lepší činnost koncového uživatele, Visual Studio může vygenerovat všechny vizuální prostředky, které moderní aplikace potřebuje pro zpracování ikon a dlaždic pro panel dlaždice a nabídku Start. Otevřete soubor *Package. appxmanifest* pro přístup k nástroji manifest Designer. Potom můžete vygenerovat všechny vizuální prostředky z dané image v projektu pouhým kliknutím na **vytvořit**.

![Snímek obrazovky návrháře manifestu v aplikaci Visual Studio](./media/deploy-modern-applications/manifest-designer.png)

Pokud otevřete kód pro soubor *Package. appxmanifest* , uvidíte několik zajímavých věcí.

Vpravo pod `<Package>` , existuje `<Identity>` uzel. V takovém případě vaše zabalená aplikace získá svoji identitu, která bude spravovaná operačním systémem.

![Uzel identity](./media/deploy-modern-applications/identity-node.png)

V `<Capabilities>` uzlu můžete najít všechny požadavky, které aplikace potřebuje, a věnovat zvláštní pozornost nástroji `<rescap:Capability Name="runFullTrust" \>` , který INSTRUUJE operační systém, aby spustil aplikaci v režimu úplné důvěryhodnosti, protože se jedná o aplikaci Win32.

![Uzel schopností](./media/deploy-modern-applications/capabilities-node.png)

Nastavte projekt balení jako spouštěný projekt pro řešení a vyberte *Spustit*. Tato akce:

- Zkompilujte aplikaci model Windows Forms.
- Vytvořte z výsledků sestavení balíček MSIX.
- Nasaďte balíčky.
- Nainstalujte ji místně na vývojovém počítači.
- Spustit aplikaci

![Naše nainstalovaná aplikace](./media/deploy-modern-applications/our-installed-application.png)

Díky tomu máte k dispozici čisté prostředí pro instalaci a odinstalaci, které MSIX poskytuje plně integrovanou do Windows 10.

Poslední fáze je o tom, jak balíček MSIX nasadit do jiného počítače.

Klikněte pravým tlačítkem na projekt balení, vyberte nabídku **úložiště** a pak vyberte možnost **vytvořit balíčky aplikací** .

Pak si můžete vybrat mezi vytvořením balíčku, který se má nahrát do Storu, nebo vytvářet balíčky pro zkušební načtení. Ve většině scénářů modernizace si zvolíte, že **chcete vytvořit balíčky pro zkušební načtení**.

![Konfigurace balíčků](./media/deploy-modern-applications/configuring-packages.png)

Můžete vybrat různé architektury, které chcete cílit, protože můžete do stejného balíčku MSIX zahrnout tolik, kolik chcete.

Posledním krokem je deklarovat, kam chcete nasadit finální prostředky instalace.

![Konfigurovat nastavení aktualizací](./media/deploy-modern-applications/configure-update-settings.png)

Na podnikových souborových serverech se můžete rozhodnout pro použití webového serveru se sdílenou cestou UNC. Věnujte pozornost nastavení, abyste určili, jak chcete aplikaci aktualizovat. Do další části budeme zabývat aktualizacemi aplikací.

Podrobný návod najdete v tématu [sbalení desktopové aplikace ze zdrojového kódu pomocí sady Visual Studio](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).

## <a name="auto-updates-in-msix"></a>Automatické aktualizace v MSIX

Windows Store má skvělý mechanismus aktualizace pomocí web Windows Update. Ve většině podnikových scénářů nepoužíváte Store k distribuci desktopových aplikací. Proto potřebujete podobný způsob konfigurace aktualizací aplikace a jejich vyžádání uživatelům.

Pomocí kombinace funkcí Windows 10 a balíčků MSIX můžete uživatelům poskytnout skvělé možnosti aktualizace. Ve skutečnosti nemusí být uživatel vůbec technický, ale bude mít k dispozici bezproblémové možnosti aktualizace aplikací.

Aktualizace pro interakci s uživatelem můžete nakonfigurovat dvěma různými způsoby:

- Aktualizace pro uživatele: operační systém zobrazuje některé automaticky vygenerované uživatelské rozhraní s dobrým uživatelským rozhraním, které uživateli oznamuje, že aplikace se chystá nainstalovat. Toto uživatelské rozhraní sestaví na základě vlastností, které zadáte na instalačních souborech.

- Tiché aktualizace na pozadí. Díky této možnosti si uživatelé nemusejí být vědomi aktualizací.

Můžete také nakonfigurovat, kdy chcete provádět aktualizace, když se aplikace spouští nebo pravidelně spouští. Díky funkcím pro načítání na straně stran můžete tyto aktualizace dokonce získat i v době, kdy je aplikace spuštěná.

Když použijete tento typ nasazení, vytvoří se speciální soubor s názvem *. instalačního programu aplikace*. Tento jednoduchý soubor obsahuje následující oddíly:

- Umístění souboru *. instalačního programu aplikace*
- Vlastnosti hlavního balíčku aplikace MSIX
- Chování aktualizace

![soubor. instalačního programu aplikace](./media/deploy-modern-applications/appinstaller-file.png)

V kombinaci s tímto souborem navrhl Microsoft speciální protokol URL pro spuštění procesu instalace z odkazu:

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

Tento protokol funguje na všech prohlížečích a spustí proces instalace s skvělým uživatelským prostředím ve Windows 10. Vzhledem k tomu, že operační systém spravuje proces instalace, ví o umístění, ze kterého byla tato aplikace nainstalována, a sleduje všechny soubory ovlivněné procesem.

MSIX vytvoří uživatelské rozhraní pro instalaci, které automaticky zobrazí některé vlastnosti balíčku. To umožňuje běžné instalační prostředí pro každou aplikaci.

Po vygenerování nového balíčku MSIX a jeho přesunutí na server nasazení stačí upravit soubor *. instalačního programu aplikace* , aby odrážel tyto změny, hlavně verzi a cestu k novému souboru MSIX. Když uživatel příště spustí aplikaci, systém bude detekovat změnu a stáhnout soubory pro novou verzi na pozadí. Až to uděláte, instalace se spustí pro uživatele, který se bude transparentně spouštět.

>[!div class="step-by-step"]
>[Předchozí](example-migration-core.md)
