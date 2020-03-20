---
title: .NET Core a open source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: b5aa42d0460d743bffe8f17a2603773c03c09ce0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181613"
---
# <a name="net-core-and-open-source"></a>Jádro .NET a open source

Tento článek obsahuje stručný přehled toho, co je jádro .NET Core, a ukazuje, jak můžete najít další informace. Úplný seznam dokumentace pro rozhraní .NET Core naleznete v [průvodci .NET Core](../../core/index.md).

## <a name="what-is-net-core"></a>Co je jádro .NET?  

.NET Core je implementace .NET Standard pro obecné účely, modulární, napříč platformami a otevřeným zdrojovým kódem. Obsahuje mnoho stejných rozhraní API jako rozhraní .NET Framework (ale .NET Core je menší sada) a obsahuje komponenty runtime, framework, kompilátor a nástroje, které podporují různé operační systémy a cíle čipů. Implementace .NET Core byla primárně řízena úlohami ASP.NET Core, ale také potřebou a touhou mít modernější implementaci. Lze jej použít ve scénářích zařízení, cloudu a vložené/IoT.  
  
Chcete-li začít s rozhraním .NET Core, navštivte .NET tutorial [Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
Hlavní charakteristiky .NET Core jsou:
  
- **Multiplatformní:** .NET Core poskytuje klíčové funkce pro implementaci funkcí aplikace, které potřebujete, a znovu použít tento kód bez ohledu na cíl vaší platformy. V současné době podporuje tři hlavní operační systémy (OS): Windows, Linux a macOS. Můžete psát aplikace a knihovny, které běží nezměněné v podporovaných operačních systémech. Seznam podporovaných operačních systémů naleznete na webu [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Open source:** .NET Core je jedním z mnoha projektů pod správou [.NET Foundation](https://www.dotnetfoundation.org/) a je k dispozici na [GitHubu](https://github.com/).  S .NET Core jako open source projekt podporuje transparentnější proces vývoje a podporuje aktivní a angažovanou komunitu.  
  
- **Flexibilní nasazení:** existují dva hlavní způsoby nasazení aplikace: nasazení závislé na rámci nebo samostatné nasazení. S nasazením závislým na rámci jsou nainstalovány pouze vaše aplikace a závislosti třetích stran a vaše aplikace závisí na celosystémové verzi .NET Core, která má být k dispozici.  S samostatné nasazení verze .NET Core používá k sestavení aplikace je také nasazenspolu s vaší aplikace a závislosti třetích stran a lze spustit vedle sebe s jinými verzemi.    Další informace naleznete v tématu [.NET Core Application Deployment](../../core/deploying/index.md).

- **Modulární:** .NET Core je modulární, protože je vydána prostřednictvím NuGet v menších montážních balíčků. Spíše než jeden velký sestavení, které obsahuje většinu základních funkcí, .NET Core je k dispozici jako menší balíčky zaměřené na funkce. To umožňuje agilnější vývojový model pro nás a umožňuje optimalizovat aplikaci tak, aby zahrnovala pouze balíčky NuGet, které potřebujete. Mezi výhody menší plochy aplikace patří přísnější zabezpečení, nižší servis, lepší výkon a nižší náklady v modelu platby za co použít.  
  
## <a name="the-net-core-platform"></a>Platforma .NET Core
  
Platforma .NET Core se skládá z několika součástí, včetně spravovaných kompilátorů, runtime, knihoven základních tříd a mnoha aplikačních modelů, jako je ASP.NET Core. Další informace o různých součástech a zapojení se získáte na následujících úložištích [GitHubu:](https://github.com/)  
  
- [.NET Core domů](https://github.com/dotnet/core)  
  
- [Runtime – platforma .NET Core a runtime](https://github.com/dotnet/runtime)  
  
- [CLI – nástroje příkazového řádku .NET Core](https://github.com/dotnet/cli)  
  
- [Roslyn - platforma kompilátoru .NET](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Viz také

- [.NET tutorial - Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Průvodce platformou .NET Core](../../core/index.md)
- [ASP.NET Základní dokumenty](/aspnet/core/)
