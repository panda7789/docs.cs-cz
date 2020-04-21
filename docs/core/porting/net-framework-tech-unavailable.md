---
title: Technologie rozhraní .NET Framework nejsou v jádru rozhraní .NET k dispozici
titleSuffix: ''
description: Informace o technologiích rozhraní .NET Framework, které nejsou k dispozici na jádru rozhraní .NET
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: 65e465f78b55270b42532eb7e8803f48c048ec3c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739144"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologie rozhraní .NET Framework nejsou v jádru rozhraní .NET k dispozici

S rozhraním .NET Core není k dispozici několik technologií dostupných pro knihovny rozhraní .NET Framework, například Domény aplikací, Vzdálená komunikace, Zabezpečení přístupu kódu (CAS), Transparentnost zabezpečení a System.EnterpriseServices. Pokud vaše knihovny spoléhají na jednu nebo více z těchto technologií, zvažte alternativní přístupy popsané níže. Další informace o kompatibilitě rozhraní API naleznete v tématu [.NET Core breaking changes](../compatibility/breaking-changes.md).

Jen proto, že rozhraní API nebo technologie není aktuálně implementována neznamená, že je záměrně nepodporované. Vyhledejte v úložištích GitHubu rozhraní .NET Core a zjistěte, jestli konkrétní problém, se kterým se setkáte, je záměrný. Pokud takový indikátor nenajdete, zasuňte problém do [úložiště dotnet/runtime](https://github.com/dotnet/runtime/issues) a požádejte o konkrétní rozhraní API a technologie. Problémy, které jsou portování požadavky jsou označeny popiskem [port-to-core.](https://github.com/dotnet/runtime/labels/port-to-core)

## <a name="appdomains"></a>Domény aplikací

Aplikační domény (AppDomains) izolují aplikace od sebe navzájem. Domény aplikací vyžadují podporu za běhu a jsou obecně drahé. Vytváření dalších domén aplikací není podporováno a v budoucnu nejsou žádné plány na přidání této funkce. Pro izolaci kódu použijte jako alternativu samostatné procesy nebo kontejnery. Chcete-li dynamicky načíst <xref:System.Runtime.Loader.AssemblyLoadContext> sestavení, použijte třídu.

Chcete-li usnadnit migraci kódu z rozhraní .NET <xref:System.AppDomain> Framework, rozhraní .NET Core zpřístupňuje některé povrchrozhraní rozhraní API. Některá řešení API fungují normálně <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>(například ), někteří členové <xref:System.AppDomain.SetCachePath%2A>nedělají nic <xref:System.PlatformNotSupportedException> (například <xref:System.AppDomain.CreateDomain%2A>) a některé z nich hodí (například ). Zkontrolujte typy, které používáte, proti [ `System.AppDomain` referenčnímu zdroji](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) v [úložišti GitHub dotnet/runtime](https://github.com/dotnet/runtime). Ujistěte se, že vyberete větev, která odpovídá implementované verzi.

## <a name="remoting"></a>Remoting

Vzdálené komunikace .NET byly identifikovány jako problematická architektura. Používá se pro komunikaci mezi doménami aplikace, která již není podporována. Vzdálené komunikace vyžaduje také podporu za běhu, která je nákladná na údržbu. Z těchto důvodů není vzdálené komunikace .NET podporována na .NET Core a nemáme v plánu na přidání podpory pro něj v budoucnu.

Pro komunikaci mezi procesy zvažte mechanismy meziprocesové komunikace (IPC) jako <xref:System.IO.Pipes> alternativu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> k vzdálené komunikace, jako je například třída nebo třída.

Napříč počítači použijte jako alternativu síťové řešení. Pokud možno použijte protokol prostého textu s nízkou režií, například HTTP. [Kestrel webový server](/aspnet/core/fundamentals/servers/kestrel), webový server používaný ASP.NET Core, je zde možnost. Zvažte také <xref:System.Net.Sockets> použití pro scénáře založené na síti, mezi počítači. Další možnosti naleznete [v tématu .NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)

Sandboxing, který se spoléhá na modul runtime nebo rámec pro omezení prostředků, které spravované aplikace nebo knihovna používá nebo spouští, [není podporován v rozhraní .NET Framework](../../framework/misc/code-access-security.md) a proto také není podporován na .NET Core. Existuje příliš mnoho případů v rozhraní .NET Framework a runtime, kde dojde ke zvýšení oprávnění pokračovat v zacházení cas jako hranice zabezpečení. Kromě toho CAS zkomplikuje implementaci a často má důsledky pro správnost a výkon pro aplikace, které nemají v úmyslu ji používat.

Pro spouštění procesů s minimální sadou oprávnění použijte hranice zabezpečení poskytované operačním systémem, jako je virtualizace, kontejnery nebo uživatelské účty.

## <a name="security-transparency"></a>Transparentnost zabezpečení

Podobně jako cas, transparentnost zabezpečení odděluje kód v izolovaném prostoru od kódu kritického pro zabezpečení deklarativním způsobem, ale [již není podporován jako hranice zabezpečení](../../framework/misc/security-transparent-code.md). Tato funkce je silně využívána programem Silverlight.

Pro spouštění procesů s nejmenší sadou oprávnění použijte hranice zabezpečení poskytované operačním systémem, jako je virtualizace, kontejnery nebo uživatelské účty.

## <a name="systementerpriseservices"></a>System.enterpriseservices

System.EnterpriseServices (COM+) není podporován a .NET Core.

## <a name="see-also"></a>Viz také

- [Přehled přenosu z rozhraní .NET Framework do jádra rozhraní .NET](../porting/index.md)
