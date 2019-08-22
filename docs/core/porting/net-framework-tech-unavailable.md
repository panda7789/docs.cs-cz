---
title: Technologie .NET Framework nedostupné v .NET Core
description: Přečtěte si o .NET Framework technologiích, které nejsou k dispozici v .NET Core
author: cartermp
ms.author: mairaw
ms.date: 04/30/2019
ms.openlocfilehash: 87c3dd337ad44fd21b255afa7c03b528cd8a42ad
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660599"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologie .NET Framework nedostupné v .NET Core

K dispozici je několik technologií pro .NET Framework knihovny, které se nedají používat s .NET Core, jako jsou AppDomains, Vzdálená komunikace, zabezpečení přístupu kódu (CAS) a transparentnost zabezpečení. Pokud se vaše knihovny spoléhají na jednu nebo více těchto technologií, vezměte v úvahu alternativní přístupy uvedené níže. Pokud chcete získat další informace o kompatibilitě rozhraní API, tým CoreFX udržuje [seznam behaviorálních změn/popisovačů kompatibility a zastaralých/zastaralých rozhraní API](https://github.com/dotnet/corefx/wiki/ApiCompat) na GitHubu.

Vzhledem k tomu, že rozhraní API nebo technologie není aktuálně implementováno, neznamená, že je záměrně Nepodporovaná. Nejdřív byste měli hledat v úložištích GitHub pro .NET Core, aby bylo možné zjistit, jestli se k určitému problému setkáte podle návrhu, ale pokud tento indikátor nemůžete najít, dejte prosím problém v [úložišti dotnet/corefx](https://github.com/dotnet/corefx/issues) na GitHubu a požádejte ho o konkrétní rozhraní API a technik. [Požadavky na port](https://github.com/dotnet/corefx/labels/port-to-core) jsou označeny `port-to-core` jmenovkou.

## <a name="appdomains"></a>AppDomains

Aplikační domény (AppDomains) izolují aplikace od sebe navzájem. Třídy AppDomains vyžadují podporu modulu runtime a jsou všeobecně poměrně nákladné. Vytváření dalších aplikačních domén se nepodporuje. Tuto možnost neplánujeme v budoucnu přidat. Pro izolaci kódu doporučujeme samostatné procesy nebo jako alternativu použít kontejnery. Pro dynamické načítání sestavení doporučujeme novou <xref:System.Runtime.Loader.AssemblyLoadContext> třídu.

Aby mohla migrace kódu z .NET Framework snazší, rozhraní .NET Core zpřístupňuje některé <xref:System.AppDomain> z ploch rozhraní API. Některá z funkcí rozhraní <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>API obvykle (například), některé členy nedělají nic ( <xref:System.AppDomain.SetCachePath%2A>například) a některé z nich <xref:System.AppDomain.CreateDomain%2A>vyvolají <xref:System.PlatformNotSupportedException> (například). Zkontrolujte typy, které používáte proti [ `System.AppDomain` zdroji odkazů](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) v [úložišti dotnet/corefx GitHub](https://github.com/dotnet/corefx), a ujistěte se, že jste vybrali větev, která odpovídá implementované verzi.

## <a name="remoting"></a>Vzdálenou

Vzdálená komunikace .NET byla označena jako problematická architektura. Používá se pro komunikaci mezi doménami, která už není podporovaná. Vzdálená komunikace také vyžaduje běhovou podporu, která je náročná na údržbu. Z těchto důvodů není vzdálená komunikace v .NET podporovaná pro .NET Core a v budoucnu neplánujeme přidat podporu pro IT.

Pro komunikaci mezi procesy zvažte jako alternativu ke vzdálené komunikaci mechanismy mezi procesy (IPC), jako je <xref:System.IO.Pipes> například <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> třída nebo.

V různých počítačích použijte jako alternativu řešení založené na síti. Nejlépe použijte protokol s malým režijním textem, jako je například HTTP. [Webový server Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), který používá ASP.NET Core, je zde možnost. Zvažte také použití <xref:System.Net.Sockets> ve scénářích pro více počítačů, které jsou založené na síti. Další možnosti naleznete v tématu [vývojářské projekty Open Source aplikace .NET: Zasílání zpráv](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)

Sandboxing, která spoléhá na modul runtime nebo na rozhraní k omezení prostředků, které spravovaná aplikace nebo knihovna používá nebo běží, se [na .NET Framework nepodporuje](../../framework/misc/code-access-security.md) , a proto se v .NET Core nepodporuje. V .NET Framework je příliš mnoho případů a modul runtime, kde se zvýšení oprávnění projeví i v případě, že se CAS považují za hranice zabezpečení. Kromě toho je implementace složitější a často má dopad na výkon aplikací, které ho nemají v úmyslu používat.

Používejte hranice zabezpečení poskytované operačním systémem, jako je virtualizace, kontejnery nebo uživatelské účty pro spouštění procesů s minimální sadou oprávnění.

## <a name="security-transparency"></a>Transparentnost zabezpečení

Podobně jako certifikační autorita, transparentnost zabezpečení odděluje kód v izolovaném prostoru z kódu kritického zabezpečení deklarativním způsobem, ale [již není podporována jako hranice zabezpečení](../../framework/misc/security-transparent-code.md). Tato funkce je silně využívána v Silverlightu. 

Používejte hranice zabezpečení poskytované operačním systémem, jako je virtualizace, kontejnery nebo uživatelské účty pro spouštění procesů s minimální sadou oprávnění.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

Rozhraní .NET Core nepodporuje System. EnterpriseServices (COM+).

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
