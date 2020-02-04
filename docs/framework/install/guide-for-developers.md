---
title: Instalace sady .NET Framework Developer Pack nebo Redistributable
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- .NET Framework redistributable package, downloading
- .NET Framework, installing
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: daf9d9d5-84ac-4bd9-a864-27665ffd0f5c
ms.openlocfilehash: 66643021ce4939505af24cf3a72ab194662a15f7
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965916"
---
# <a name="install-the-net-framework-for-developers"></a>Instalace .NET Framework pro vývojáře

.NET je nedílnou součástí mnoha aplikací běžících na Windows a poskytuje společné funkce pro spouštění těchto aplikací. Pro vývojáře .NET Framework poskytuje komplexní a konzistentní programovací model pro vytváření aplikací, které mají vizuálně působivé uživatelské prostředí a bezproblémové a zabezpečené komunikace.

> [!NOTE]
> Toto téma je určené pro **vývojáře** , kteří chtějí nainstalovat .NET Framework do svého vlastního systému, nebo si ho chtějí nainstalovat s aplikacemi. Pro **uživatele** , kteří mají zájem o instalaci .NET Framework, přečtěte si jednotlivá témata týkající se instalace .NET Framework na konkrétní operační systémy, jako je například [instalace .NET Framework ve Windows 10 a Windows Server 2016](on-windows-10.md).

Tento článek obsahuje odkazy na instalaci všech verzí .NET Framework z .NET Framework 4,5 až do .NET Framework 4,8 v počítači. Pokud jste vývojář, můžete tyto odkazy použít také ke stažení a distribuci .NET Framework s vašimi aplikacemi. Informace o nasazení verze .NET Framework s vaší aplikací najdete v [Průvodci nasazením .NET Framework pro vývojáře](../deployment/deployment-guide-for-developers.md).

[!INCLUDE[net-framework-4-versions](../../../includes/net-framework-4x-versions.md)]

Další informace o verzích .NET Framework a o tom, jak určit, které verze jsou nainstalovány v počítači, naleznete v tématu [verze a závislosti](../migration-guide/versions-and-dependencies.md) a [Postupy: určení, které verze .NET Framework jsou nainstalovány](../migration-guide/how-to-determine-which-versions-are-installed.md).

> [!NOTE]
> Informace o .NET Framework 3,5 najdete v tématu [instalace .NET Framework 3,5 ve Windows 10, Windows 8.1 a Windows 8](dotnet-35-windows-10.md).

Použijte následující tabulku pro rychlé odkazy nebo si přečtěte podrobnosti. Chcete-li zobrazit požadavky na systém pro .NET Framework před instalací, přečtěte si téma [požadavky na systém](../get-started/system-requirements.md). Pomoc při řešení potíží najdete v tématu [řešení potíží](troubleshoot-blocked-installations-and-uninstallations.md).

| Verze rozhraní .NET Framework | Instalační program (sada Developer Pack a modul runtime) | Podpora platforem |
| ---------------------- | -------------------------------------- | ---------------- |
|**4,8**   | [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)    | **Zahrnuto v:**<br/><br/>Windows 10 Květen 2019 Update<br/>[Visual Studio 2019 (aktualizace 16,3)](https://my.visualstudio.com/Downloads?q=visual%20studio%202017)<br/><br/> **Můžete nainstalovat na:**<br/><br/>Windows 10 říjen 2018 – aktualizace<br/>Aktualizace Windows 10. dubna 2018<br/>Aktualizace Creators v systému Windows 10<br/>Windows 10 Creators Update <br /> Windows 10 Anniversary Update<br /> Windows 8.1 a starší<br /> Windows Server. 2019<br/>Windows Server verze 1809<br/>Windows Server verze 1803<br /><br/> (úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))||
|**4.7.2** | [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472) | **Zahrnuto v:** <br/><br/>Windows 10 říjen 2018 – aktualizace<br/>Aktualizace Windows 10. dubna 2018<br/>Windows Server. 2019<br/>Windows Server verze 1809<br/>Windows Server verze 1803<br/>[Visual Studio 2017 (aktualizace 15,8)](https://my.visualstudio.com/Downloads?q=visual%20studio%202017)<br/><br/> **Můžete nainstalovat na:**<br/> <br/>Aktualizace Creators v systému Windows 10<br/>Windows 10 Creators Update <br /> Windows 10 Anniversary Update<br /> Windows 8.1 a starší<br /> Windows Server verze 1709 a starší<br /><br/> (úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))||
|**4.7.1** | [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471) | **Zahrnuto v:** <br/><br/>Aktualizace Creators v systému Windows 10<br/>Windows Server verze 1709<br/>[Visual Studio 2017 (aktualizace 15,5)](https://my.visualstudio.com/Downloads?q=visual%20studio%202017)<br/><br/> **Můžete nainstalovat na:**<br/><br/> Windows 10 Creators Update <br /> Windows 10 Anniversary Update<br /> Windows 8.1 a starší<br /> Windows Server 2016 a starší<br /> (úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))||
|**4.7**   | [.NET Framework 4,7](https://dotnet.microsoft.com/download/dotnet-framework/net47)    | **Zahrnuto v:** <br/><br/>Windows 10 Creators Update<br/>[Visual Studio 2017 (aktualizace 15,3)](https://my.visualstudio.com/Downloads?q=visual%20studio%202017)<br/><br/> **Můžete nainstalovat na:**<br /><br/> Windows 10 Anniversary Update<br /> Windows 8.1 a starší<br /> Windows Server 2016 a starší<br /> (úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))||
|**4.6.2** | [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462) | **Zahrnuto v:** <br/><br/>Windows 10 Anniversary Update<br /><br /> **Můžete nainstalovat na:**<br /><br/> Listopadová aktualizace pro Windows 10 <br/> Windows 10 <br /> Windows 8.1 a starší<br /> Windows Server 2012 R2 a starší<br /> (úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))|
|**4.6.1** | [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461) | **Zahrnuto v:** <br/><br/>[Visual Studio 2015 Update 2](https://my.visualstudio.com/Downloads?q=visual%20studio%202015)<br/><br/>**Můžete nainstalovat na:**<br /><br/> Windows 10 <br /> Windows 8.1 a starší<br /> Windows Server 2012 R2 a starší<br /> (úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))|
|**4.6**   | [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)    | **Zahrnuto v:** <br/><br/> Windows 10 <br />[Visual Studio 2015](https://my.visualstudio.com/Downloads?q=visual%20studio%202015)<br /><br /> **Můžete nainstalovat na:**<br /><br/> Windows 8.1 a starší<br /> Windows Server 2012 R2 a starší<br /> (úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))|
|**4.5.2** | [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452) | **Můžete nainstalovat na:**<br/><br/> Windows 8.1 a starší<br /> Windows Server 2012 R2 a starší<br /> (úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))|
|**4.5.1** | [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451) | **Zahrnuto v:**<br/><br/>Windows 8.1<br /> Windows Server 2012 R2<br /> [Visual Studio 2013](https://my.visualstudio.com/Downloads?q=visual%20studio%202013)<br /><br /> **Můžete nainstalovat na:**<br /><br/> Windows 8 a starší<br /> Windows Server 2012 a starší<br />(úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))|
|**4.5**   | [.NET Framework 4,5](https://dotnet.microsoft.com/download/dotnet-framework/net45)    | **Zahrnuto v:** <br/><br/>Windows 8<br /> Windows Server 2012<br /> [Visual Studio 2012](https://my.visualstudio.com/Downloads?q=visual%20studio%202012)<br /><br /> **Můžete nainstalovat na:**<br/><br /> Windows 7 a starší<br /> Windows Server 2008 SP2 a starší<br />(úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md))|

**Sadu Developer Pack** můžete nainstalovat na určitou verzi .NET Framework, pokud je k dispozici na všech podporovaných platformách.

**Web nebo offline instalační program** můžete nainstalovat na:

- Windows 8.1 a starší

- Windows Server 2012 R2 a starší

Úplný seznam najdete v tématu [požadavky na systém](../get-started/system-requirements.md).

Obecný úvod k .NET Framework pro uživatele a vývojáře naleznete v tématu [Začínáme](../get-started/index.md). Informace o nasazení .NET Framework s vaší aplikací najdete v [Průvodci nasazením](../deployment/deployment-guide-for-developers.md). Informace o architektuře a klíčových funkcích .NET Framework najdete v [přehledu](../get-started/overview.md).

## <a name="installation-choices"></a>Možnosti instalace

Nainstalujte sadu targeting Developer Pack pro vývoj na nejnovější verzi .NET Framework v sadě Visual Studio nebo v jiném vývojovém prostředí nebo si stáhněte .NET Framework distribuovatelné pro distribuci s vaší aplikací nebo ovládacím prvkem.

### <a name="to-install-the-net-framework-developer-pack-or-targeting-pack"></a>Instalace sady .NET Framework Developer Pack nebo sady targeting pack

*Sada targeting pack* umožňuje vaší aplikaci cílit na konkrétní verzi .NET Framework při vývoji v sadě Visual Studio a některých jiných vývojových prostředích. Sada *Developer Pack* zahrnuje konkrétní verzi .NET Framework a její doprovodnou sadu SDK spolu s odpovídajícím balíčkem targeting pack.

Sada Developer Pack pro .NET Framework 4.5.1 nebo 4.5.2, sada Targeting Pack for .NET Framework 4,6 a sada Developer Pack pro .NET Framework 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8 poskytuje konkrétní verzi .NET Framework referenčních sestavení, jazyk sady a soubory IntelliSense pro použití v integrovaném vývojovém prostředí, jako je například Visual Studio.  Pokud používáte sadu Visual Studio, sada Developer Pack nebo sada targeting pack také přidá nainstalovanou verzi .NET Framework k cílovým volbám při vytváření nového projektu.  Vyberte jednu z následujících možností:

- [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
- [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
- [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
- [.NET Framework 4,7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
- [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
- [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
- [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
- [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452) pro instalaci verze 4.5.2 do Windows 8.1 nebo starší verze, Visual Studio 2013, Visual Studio 2012 nebo jiné IDES.
- [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451) k instalaci verze 4.5.1 pro Visual Studio 2012 nebo jiné IDES.

Na stránce stažení sady Developer Pack vyberte možnost **Stáhnout**. Dále vyberte možnost **Spustit** nebo **Uložit**a po zobrazení výzvy postupujte podle pokynů. Můžete také nainstalovat sadu Developer Pack nebo sadu targeting pack pro konkrétní verzi .NET Framework tím, že ji vyberete z volitelných komponent v úloze **vývoj desktopových aplikací .NET** v instalační program pro Visual Studio, jak ukazuje následující obrázek.

   ![Instalační program pro Visual Studio s úlohou vývoj desktopových aplikací .NET](./media/visual-studio-installer.jpg)

Při cílení na konkrétní verzi .NET Framework je aplikace sestavena pomocí referenčních sestavení, která jsou součástí sady Developer Pack dané verze. V době běhu jsou sestavení přeložena z globální mezipaměti sestavení (GAC) a referenční sestavení nejsou použita.

Při sestavování aplikace ze sady Visual Studio nebo použití nástroje MSBuild z příkazového řádku může nástroj MSBuild zobrazit chybu MSB3644, "referenční sestavení pro architekturu"*Framework-Version*"nebyla nalezena." Chcete-li tuto chybu vyřešit, Stáhněte sadu Developer Pack nebo sadu Target Pack pro danou verzi .NET Framework.

### <a name="to-install-or-download-the-net-framework-redistributable"></a>Instalace nebo stažení .NET Framework redistributable

Instalační programy stáhnou .NET Framework komponenty pro aplikaci nebo ovládací prvek, který cílí na tyto verze .NET Framework. Tyto komponenty musí být nainstalovány v každém počítači, kde běží aplikace nebo ovládací prvek. Tyto instalační programy jsou distribuovatelné, takže je můžete zahrnout do instalačního programu pro vaši aplikaci.

Stránka pro stažení je k dispozici v několika jazycích, ale většina souborů ke stažení je k dispozici pouze v angličtině. Pro další jazykovou podporu je nutné nainstalovat jazykovou sadu.

K dispozici jsou dva typy redistribuovatelných instalačních programů:

- **Webový instalátor** (webový zaváděcí nástroj) stáhne požadované součásti a jazykové sady, které odpovídají operačnímu systému instalačního počítače z webu. Tento balíček je mnohem menší než instalační program v režimu offline, ale vyžaduje konzistentní připojení k Internetu. Můžete stáhnout [samostatné jazykové sady](#to-install-language-packs) pro instalaci další jazykové podpory.

- **Instalační program v režimu offline** (samostatný Distribuovatelný) obsahuje všechny součásti potřebné pro instalaci .NET Framework, ale neobsahuje jazykové sady. Tento soubor ke stažení je větší než webový instalační program. Instalační program v režimu offline nevyžaduje připojení k Internetu. Po spuštění offline instalátoru můžete stáhnout [samostatné jazykové sady](#to-install-language-packs) pro instalaci jazykové podpory. Pokud nemůžete spoléhat na konzistentní připojení k Internetu, použijte instalační program v režimu offline.

Webové i offline instalační programy jsou navržené pro počítače na platformě x86 a x64 (viz [požadavky na systém](../get-started/system-requirements.md)), ale nepodporují počítače s procesorem Itanium.

1. Otevřete stránku pro stažení .NET Framework verze, kterou chcete nainstalovat:

   - [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
   - [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
   - [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
   - [.NET Framework 4,7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
   - [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
   - [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
   - [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
   - [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
   - [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
   - [.NET Framework 4,5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

1. Vyberte jazyk pro stránku pro stažení. Tato možnost nestáhne lokalizované prostředky .NET Framework; ovlivňuje pouze text zobrazený na stránce pro stahování.

1. Klikněte na tlačítko **Stáhnout**.

1. Pokud se zobrazí výzva, vyberte stažený soubor, který odpovídá vaší architektuře systému, a pak zvolte **Další**.

1. Po zobrazení výzvy ke stažení proveďte **jednu** z následujících akcí:

   - Chcete-li nainstalovat .NET Framework do počítače, zvolte možnost **Spustit**a poté postupujte podle pokynů na obrazovce.

   - Pokud chcete stáhnout .NET Framework pro opětovnou distribuci, zvolte **Uložit**a pak postupujte podle pokynů na obrazovce.

1. Pokud chcete stáhnout prostředky pro další jazyky, postupujte podle pokynů v následující části a nainstalujte jednu nebo více jazykových sad.

> [!NOTE]
> Pokud narazíte na problémy při instalaci, přečtěte si téma [řešení potíží](troubleshoot-blocked-installations-and-uninstallations.md).

**Poznámky k instalaci:**

- .NET Framework 4,5 a novější verze nahrazují .NET Framework 4,0. Při instalaci těchto verzí do systému, který má nainstalován .NET Framework 4, budou sestavení nahrazena.

- Odinstalace .NET Framework 4,5 nebo novějších verzí také odstraní existující soubory .NET Framework 4. Pokud se chcete vrátit na .NET Framework 4, je nutné ji znovu nainstalovat a všechny její aktualizace. Viz [instalace .NET Framework 4](https://go.microsoft.com/fwlink/p/?LinkId=230665).

- K instalaci .NET Framework 4,5 nebo novějších verzí musíte mít přihlašovací údaje správce.

- Distribuovatelný balíček .NET Framework 4,5 byl od 9. října 2012 aktualizován, aby opravil problém týkající se nesprávného časového razítka v digitálním certifikátu, což způsobilo, že digitální podpis u souborů vytvořených a podepsaných společností Microsoft vyprší předčasně. Pokud jste dříve nainstalovali balíček .NET Framework 4,5 Redistributable, který je vydaný 16. srpna 2012, doporučujeme, abyste aktualizovali kopii pomocí nejnovější distribuovatelné stránky ze [stránky pro stažení .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/net45). Další informace o tomto problému najdete v článku znalostní báze [Microsoft Security advisor 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655) a [Knowledge Base 2770445](https://support.microsoft.com/kb/2770445).

## <a name="to-install-language-packs"></a>Instalace jazykových sad

Jazykové sady jsou spustitelné soubory, které obsahují lokalizované prostředky (například přeložené chybové zprávy a text uživatelského rozhraní) pro podporované jazyky. Pokud nenainstalujete jazykovou sadu, .NET Framework chybové zprávy a další text se zobrazí v angličtině.  Všimněte si, že webová instalační služba automaticky nainstaluje jazykovou sadu odpovídající vašemu operačnímu systému, ale do svého počítače můžete stáhnout další jazykové sady. Offline instalátory neobsahují žádné jazykové sady.

> [!IMPORTANT]
> Jazykové sady neobsahují .NET Framework komponenty, které jsou nutné ke spuštění aplikace, takže před instalací jazykové sady je nutné spustit webový nebo offline instalační program. Pokud jste již nainstalovali jazykovou sadu, odinstalujte ji, nainstalujte .NET Framework a pak znovu nainstalujte jazykovou sadu.

1. Otevřete stránku pro stažení jazykové sady pro .NET Framework verzi, kterou jste nainstalovali:

   - [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)
   - [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)
   - [.NET Framework 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471)
   - [.NET Framework 4,7](https://dotnet.microsoft.com/download/dotnet-framework/net47)
   - [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)
   - [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)
   - [.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)
   - [.NET Framework 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452)
   - [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/net451)
   - [.NET Framework 4,5](https://dotnet.microsoft.com/download/dotnet-framework/net45)

2. V seznamu jazyk vyberte jazyk, který chcete stáhnout, a počkejte několik sekund, než se stránka znovu načte do daného jazyka.

3. Klikněte na tlačítko **Stáhnout**.

V následující tabulce jsou uvedeny podporované jazyky.

| Jazyk              | Jazyková verze |
| --------------------- | :-----: |
| Arabština                | snížen      |
| Čeština                 | cs      |
| dánština                | da      |
| Nizozemština                 | nl      |
| Finština               | fi      |
| Angličtina (USA)         | en-US   |
| Francouzština                | fr      |
| Němčina                | &      |
| Řečtina                 | el      |
| Hebrejština                | uvede      |
| Maďarština             | hu      |
| Italština               | její      |
| Japonština              | dža      |
| Korejština                | Ko      |
| norština             | Ne      |
| Polština                | pl      |
| Portugalština (Brazílie)   | pt-BR   |
| Portugalština (Portugalsko) | pt-PT   |
| Ruština               | ru      |
| Zjednodušená čínština    | zh-CHS  |
| Španělština               | jednomu      |
| švédština               | sv      |
| Tradiční čínština   | zh-CHT  |
| Turečtina               | recenzent      |

## <a name="next-steps"></a>Další kroky

- Pokud s .NET Frameworkem začínáte, přečtěte si [Přehled](../get-started/overview.md) úvodu k klíčovým koncepcím a komponentám.

- Nové funkce a vylepšení .NET Framework 4,5 a všech novějších verzích najdete v tématu [co je nového](../whats-new/index.md).

- Podrobné informace o nasazení .NET Framework s vaší aplikací najdete v tématu [Průvodce nasazením pro vývojáře](../deployment/deployment-guide-for-developers.md).

- Změny, které mají vliv na nasazení .NET Framework s vaší aplikací, najdete v tématu [zmenšování restartu systému během instalace .NET Framework 4,5](../deployment/reducing-system-restarts.md).

- Informace o migraci vaší aplikace z .NET Framework 4 na .NET Framework 4,5 a novějších verzích najdete v [Průvodci migrací](../migration-guide/index.md).

- V tématu [.NET Framework reference source](https://referencesource.microsoft.com/) můžete procházet .NET Framework zdrojového kódu v režimu online. Zdroj odkazů je také k dispozici na [GitHubu](https://github.com/Microsoft/referencesource). Můžete [Stáhnout referenční zdroj](https://referencesource.microsoft.com/download.html) pro zobrazení v režimu offline a procházet zdroje (včetně oprav a aktualizací) během ladění. Další informace najdete v blogu o [novém hledání zdroje odkazů .NET](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).

## <a name="see-also"></a>Viz také:

- [Průvodce nasazením pro vývojáře](../deployment/deployment-guide-for-developers.md)
- [Příručka nasazení pro administrátory](../deployment/guide-for-administrators.md)
- [Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8](dotnet-35-windows-10.md)
- [Řešení potíží se zablokovanými .NET Framework instalací a odinstalací](troubleshoot-blocked-installations-and-uninstallations.md)
