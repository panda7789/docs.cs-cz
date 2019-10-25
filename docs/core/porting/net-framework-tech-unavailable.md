---
title: Technologie .NET Framework nedostupné v .NET Core
description: Přečtěte si o .NET Framework technologiích, které nejsou k dispozici v .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: e5626d7b3e402848e2e84c49d4e98e109f62982d
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846814"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologie .NET Framework nedostupné v .NET Core

K dispozici je několik technologií pro .NET Framework knihovny, které se nedají používat s .NET Core, jako jsou AppDomains, Vzdálená komunikace, zabezpečení přístupu kódu (CAS) a transparentnost zabezpečení. Pokud se vaše knihovny spoléhají na jednu nebo více těchto technologií, vezměte v úvahu alternativní přístupy uvedené níže. Další informace o kompatibilitě rozhraní API najdete v článku o [nejnovějších změnách .NET Core](../compatibility/breaking-changes.md) .

Vzhledem k tomu, že rozhraní API nebo technologie není aktuálně implementováno, neznamená, že je záměrně Nepodporovaná. Nejdřív byste měli hledat v úložištích GitHub pro .NET Core, aby bylo možné zjistit, jestli se k určitému problému setkáte podle návrhu, ale pokud tento indikátor nemůžete najít, dejte prosím problém v [úložišti dotnet/corefx](https://github.com/dotnet/corefx/issues) na GitHubu a požádejte ho o konkrétní rozhraní API a technik. [Požadavky na porty](https://github.com/dotnet/corefx/labels/port-to-core) jsou označené `port-to-core` popisku.

## <a name="appdomains"></a>Objektů třídy AppDomains

Aplikační domény (AppDomains) izolují aplikace od sebe navzájem. Třídy AppDomains vyžadují podporu modulu runtime a jsou všeobecně poměrně nákladné. Vytváření dalších aplikačních domén se nepodporuje. Tuto možnost neplánujeme v budoucnu přidat. Pro izolaci kódu doporučujeme samostatné procesy nebo jako alternativu použít kontejnery. Pro dynamické načítání sestavení doporučujeme novou třídu <xref:System.Runtime.Loader.AssemblyLoadContext>.

Aby mohla migrace kódu z .NET Framework snazší, rozhraní .NET Core zpřístupňuje některé z ploch rozhraní API <xref:System.AppDomain>. Některá z funkcí rozhraní API obvykle (například <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), některé členy nedělají nic (například <xref:System.AppDomain.SetCachePath%2A>) a některé z nich vyvolají <xref:System.PlatformNotSupportedException> (například <xref:System.AppDomain.CreateDomain%2A>). Zkontrolujte typy, které používáte, na [zdrojovém odkazu`System.AppDomain`](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) v [úložišti GitHub/corefx](https://github.com/dotnet/corefx), a ujistěte se, že jste vybrali větev, která odpovídá implementované verzi.

## <a name="remoting"></a>Vzdálenou

Vzdálená komunikace .NET byla označena jako problematická architektura. Používá se pro komunikaci mezi doménami, která už není podporovaná. Vzdálená komunikace také vyžaduje běhovou podporu, která je náročná na údržbu. Z těchto důvodů není vzdálená komunikace v .NET podporovaná pro .NET Core a v budoucnu neplánujeme přidat podporu pro IT.

Pro komunikaci mezi procesy zvažte jako alternativu ke vzdálené komunikaci mechanismy mezi procesy (IPC), jako je například <xref:System.IO.Pipes> nebo třída <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>.

V různých počítačích použijte jako alternativu řešení založené na síti. Nejlépe použijte protokol s malým režijním textem, jako je například HTTP. [Webový server Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), který používá ASP.NET Core, je zde možnost. Zvažte také použití <xref:System.Net.Sockets> pro scénáře pro více počítačů, které jsou založené na síti. Další možnosti naleznete v tématu [vývojářské projekty Open Source aplikace .NET: zasílání zpráv](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)

Sandboxing, která spoléhá na modul runtime nebo na rozhraní k omezení prostředků, které spravovaná aplikace nebo knihovna používá nebo běží, se [na .NET Framework nepodporuje](../../framework/misc/code-access-security.md) , a proto se v .NET Core nepodporuje. V .NET Framework je příliš mnoho případů a modul runtime, kde se zvýšení oprávnění projeví i v případě, že se CAS považují za hranice zabezpečení. Kromě toho je implementace složitější a často má dopad na výkon aplikací, které ho nemají v úmyslu používat.

Používejte hranice zabezpečení poskytované operačním systémem, jako je virtualizace, kontejnery nebo uživatelské účty pro spouštění procesů s minimální sadou oprávnění.

## <a name="security-transparency"></a>Transparentnost zabezpečení

Podobně jako certifikační autorita, transparentnost zabezpečení odděluje kód v izolovaném prostoru z kódu kritického zabezpečení deklarativním způsobem, ale [již není podporována jako hranice zabezpečení](../../framework/misc/security-transparent-code.md). Tato funkce je silně využívána v Silverlightu. 

Používejte hranice zabezpečení poskytované operačním systémem, jako je virtualizace, kontejnery nebo uživatelské účty pro spouštění procesů s minimální sadou oprávnění.

## <a name="systementerpriseservices"></a>System. EnterpriseServices

Rozhraní .NET Core nepodporuje System. EnterpriseServices (COM+).

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
