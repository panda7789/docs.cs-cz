---
title: .NET Core a open source
description: Přečtěte si přehled o .NET Core, což je Obecná implementace .NET Standard pro obecné účely, pro různé platformy a open source.
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 08d30d047c25b3b6d681d72b46b81a0cb21f8e0a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622754"
---
# <a name="net-core-and-open-source"></a>.NET Core a open source

Tento článek poskytuje stručný přehled toho, co je .NET Core, a ukazuje, jak můžete najít další informace. Úplný seznam dokumentace pro .NET Core najdete v [průvodci .NET Core](../../core/index.yml).

## <a name="what-is-net-core"></a>Co je .NET Core?  

.NET Core je univerzální účelem implementace .NET Standard pro různé platformy a open source. Obsahuje mnoho ze stejných rozhraní API jako .NET Framework (ale .NET Core je menší sada) a zahrnuje součásti modulu runtime, architektury, kompilátoru a nástrojů, které podporují různé operační systémy a cíle čipu. Implementace .NET Core byla primárně řízena ASP.NET Core úlohami, ale také potřebou a přáním o moderní implementaci. Dá se použít v scénářích zařízení, Cloud a integrovaných a IoT.  
  
Pokud chcete začít pracovat s .NET Core, přejděte do kurzu .NET [Hello World během 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
Hlavními charakteristikami .NET Core jsou:
  
- Pro **různé platformy:** .NET Core poskytuje klíčovou funkci pro implementaci funkcí aplikace, které potřebujete, a opakované použití tohoto kódu bez ohledu na cíl vaší platformy. Aktuálně podporuje tři hlavní operační systémy (OS): Windows, Linux a macOS. Můžete psát aplikace a knihovny, které běží beze změny v podporovaných operačních systémech. Seznam podporovaných operačních systémů najdete v článku [Přehled .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Open Source:** .NET Core je jedním z mnoha projektů v Stewardship [rozhraní .NET Foundation](https://www.dotnetfoundation.org/) a je k dispozici na [GitHubu](https://github.com/). .NET Core jako open source projekt podporuje pokročilejší proces vývoje a aktivní a spolupracující komunitu.  
  
- **Flexibilní nasazení:** existují dva hlavní způsoby nasazení aplikace: nasazení závislé na rozhraní nebo samostatné nasazení. Při nasazení závislém na rozhraní se nainstalují jenom vaše aplikace a závislosti třetích stran a vaše aplikace závisí na verzi .NET Core, která je pro systém platná. Pomocí samostatně nasazeného nasazení se také nasadí verze .NET Core, která se používá k sestavení vaší aplikace, spolu s vašimi aplikacemi a závislostmi třetích stran a může běžet souběžně s jinými verzemi. Další informace najdete v tématu [nasazení aplikace .NET Core](../../core/deploying/index.md).

- **Modulární:** modul .NET Core je modulární, protože je vydaný prostřednictvím NuGet v menších balíčcích sestavení. Místo jednoho velkého sestavení, které obsahuje většinu základních funkcí, je .NET Core dostupné jako menší balíčky orientované na funkce. Tato modularita umožňuje pružnější model vývoje pro nás a umožňuje optimalizovat aplikaci tak, aby zahrnovala jenom balíčky NuGet, které potřebujete. Výhody menšího povrchu aplikace zahrnují důkladné zabezpečení, omezenou údržbu, vyšší výkon a snížené náklady v modelu průběžných plateb.  
  
## <a name="the-net-core-platform"></a>Platforma .NET Core
  
Platforma .NET Core se skládá z několika komponent, včetně spravovaných kompilátorů, modulu runtime, knihoven základních tříd a mnoha modelů aplikací, jako je ASP.NET Core. Další informace o různých součástech a o tom, jak se zabývají, najdete v následujících úložištích [GitHub](https://github.com/) :  
  
- [Domovská stránka .NET Core](https://github.com/dotnet/core)  
  
- [Runtime – platforma .NET Core a modul runtime](https://github.com/dotnet/runtime)  
  
- [CLI – nástroje příkazového řádku .NET Core](https://github.com/dotnet/cli)  
  
- [Roslyn – .NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Viz také:

- [Kurz pro .NET – Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Průvodce platformou .NET Core](../../core/index.yml)
- [ASP.NET Core docs](/aspnet/core/)
