---
title: Technologií rozhraní .NET framework není k dispozici v rozhraní .NET Core
description: Seznamte se s technologií rozhraní .NET Framework, které jsou k dispozici v rozhraní .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: be55cd1d1c67b0542c8474d1b2e47f6752f658a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663138"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologií rozhraní .NET framework není k dispozici v rozhraní .NET Core

Několik technologií, které jsou k dispozici pro knihovny rozhraní .NET Framework nejsou k dispozici pro použití s .NET Core, jako je například objektů třídy AppDomains, vzdálené komunikace, zabezpečení přístupu kódu (CAS) a transparentnost zabezpečení. Pokud vaše knihovny spoléhat na jeden nebo více z těchto technologií, vezměte v úvahu alternativních přístupů popsaných níže. Další informace o kompatibilitě rozhraní API CoreFX tým udržuje [seznam konce změny/compat chování a zastaralé nebo starší verze rozhraní API](https://github.com/dotnet/corefx/wiki/ApiCompat) v Githubu.

To, že rozhraní API nebo technologie v současnosti není implementovaná nebude neznamená, že má nepodporovanou záměrně. By měli nejdřív vyhledat úložiště GitHub pro .NET Core, pokud chcete zobrazit, pokud konkrétní problém narazíte je záměrné, ale pokud nemůžete najít takový ukazatel, požádejte prosím problém ve službě [úložišti dotnet/corefx problémy](https://github.com/dotnet/corefx/issues) v Githubu požádat pro konkrétní rozhraní API a technologií. [Portování požadavky otázky](https://github.com/dotnet/corefx/labels/port-to-core) jsou označené `port-to-core` popisek.

## <a name="appdomains"></a>AppDomains

Domény aplikace (AppDomains) izolace aplikace od sebe. Objektů třídy AppDomains vyžadují podpora modulu CLR a obvykle jsou dost drahé. Nepodporuje vytváření domén další aplikace... Plánujeme není na přidání této funkce v budoucnu. Izolace kódu, doporučujeme samostatné procesy nebo pomocí kontejnerů jako alternativu. Pro dynamické načítání sestavení, doporučujeme vám nový <xref:System.Runtime.Loader.AssemblyLoadContext> třídy.

Pro usnadnění migrace kódu z rozhraní .NET Framework, .NET Core uvádí některé <xref:System.AppDomain> rovinu rozhraní API. Některá rozhraní API normálně fungovat (například <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), některé členy Neprovádět žádnou akci (třeba <xref:System.AppDomain.SetCachePath%2A>), a některé z nich výjimku <xref:System.PlatformNotSupportedException> (například <xref:System.AppDomain.CreateDomain%2A>). Zkontrolujte typy použít proti [ `System.AppDomain` zdroj odkazu](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) v [úložiště GitHub dotnet/corefx](https://github.com/dotnet/corefx)a vyberte větev, která odpovídá verzi implementovaná.

## <a name="remoting"></a>Vzdálená komunikace

Vzdálené komunikace .NET byla identifikována jako problematické architektury. Používá se pro komunikaci mezi domény aplikace, které se už nepodporuje. Vzdálená komunikace také vyžaduje podpora modulu CLR, které je náročné na údržbu. Z těchto důvodů se nepodporuje vzdálené komunikace .NET na .NET Core a není plánujeme v budoucnu doplnění podpory pro něj.

Komunikace mezi procesy, vezměte v úvahu mechanismus meziprocesové komunikace (IPC) jako alternativu k vzdálené komunikace, jako <xref:System.IO.Pipes> nebo <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> třídy.

V počítačích použijte jako alternativu řešení založené na síti. Pokud možno použijte protokol s nízkou režií prostého textu, jako je například HTTP. [Kestrel webový server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), webový server používá ASP.NET Core, je možnost tady. Také zvážit použití <xref:System.Net.Sockets> pro scénáře založené na síti, mezi počítači. Další možnosti najdete v tématu [.NET Open Source projektů pro vývojáře: Zasílání zpráv](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)

Izolace (sandbox), které spoléhá na modul runtime nebo rozhraní, chcete-li omezit které prostředky spravované aplikace nebo knihovna používá nebo běží, [není podporován v rozhraní .NET Framework](~/docs/framework/misc/code-access-security.md) a proto se taky nepodporuje v rozhraní .NET Core. Nejsou moc velký počet případů v rozhraní .NET Framework a modulu runtime kde dojde k zvýšení oprávnění pokračovat zpracování certifikační Autority jako hranice zabezpečení. Certifikační Autority navíc díky implementaci složitější a často má vliv na správnost výkon pro aplikace, které nechcete použít.

Volit raději hranice zabezpečení poskytované operačního systému, například virtualizace, kontejnerů nebo uživatelské účty pro spouštění procesů s minimální sadu oprávnění.

## <a name="security-transparency"></a>Transparentnost zabezpečení

Podobně jako u certifikační Autority, transparentnost zabezpečení ze zabezpečení kritického kódu deklarativní způsobem odděluje kódu v izolovaném prostoru, ale je [již nejsou podporovány jako hranice zabezpečení](~/docs/framework/misc/security-transparent-code.md). Tato funkce je nejčastěji používá program Silverlight. 

Volit raději hranice zabezpečení poskytované operačního systému, například virtualizace, kontejnerů nebo uživatelské účty pro spouštění procesů s nejmenší sadu oprávnění.

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
