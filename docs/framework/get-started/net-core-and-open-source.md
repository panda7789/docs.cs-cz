---
title: .NET Core a open source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ad74a70fff9916dc66bb4d2eacbdaf40cb241c3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853959"
---
# <a name="net-core-and-open-source"></a>.NET Core a open source
Toto téma poskytuje stručný přehled toho, co je .NET Core, a ukazuje, jak můžete najít další informace. Úplný seznam témat pro .NET Core najdete v [průvodci .NET Core](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>Co je .NET Core?  
 .NET Core je univerzální účelem, modulární, pro více platforem a open source implementaci .NET Standard. Obsahuje mnoho ze stejných rozhraní API jako .NET Framework (ale .NET Core je menší sada) a obsahuje komponenty modulu runtime, architektury, kompilátoru a nástrojů, které podporují různé operační systémy a cíle čipu. Implementace .NET Core byla primárně řízena ASP.NET Core úlohami, ale také potřebou a přáním o moderní implementaci. Dá se použít v scénářích zařízení, cloudu a integrovaných a IoT.  
  
 Pokud chcete začít pracovat s .NET Core, přejděte do kurzu .NET [Hello World během 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
 Tady jsou hlavní charakteristiky .NET Core:  
  
- Pro **různé platformy:** .NET Core poskytuje klíčovou funkci pro implementaci funkcí aplikace, které potřebujete, a opakované použití tohoto kódu bez ohledu na cíl vaší platformy. V současné době podporuje tři hlavní operační systémy (OS): Windows, Linux a macOS. Můžete psát aplikace a knihovny, které běží beze změny v podporovaných operačních systémech. Seznam podporovaných operačních systémů najdete v článku [Přehled .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Open Source:** .NET Core je jedním z mnoha projektů v Stewardship [rozhraní .NET Foundation](https://www.dotnetfoundation.org/) a je k dispozici na [GitHubu](https://github.com/).  Rozhraní .NET Core jako open source projekt podporuje pokročilejší proces vývoje a podporuje aktivní a spolupracující komunitu.  
  
- **Flexibilní nasazení:** existují dva hlavní způsoby nasazení aplikace: nasazení závislé na rozhraní nebo samostatné nasazení. Při nasazení závislém na rozhraní se nainstalují jenom vaše aplikace a závislosti třetích stran a vaše aplikace závisí na verzi .NET Core, která je pro systém platná.  Pomocí samostatně nasazeného nasazení je verze .NET Core, která se používá k sestavení vaší aplikace, nasazená taky společně s vašimi aplikacemi a závislostmi třetích stran a můžou běžet souběžně s jinými verzemi.    Další informace najdete v tématu [nasazení aplikace .NET Core](../../core/deploying/index.md).

- **Modulární:** modul .NET Core je modulární, protože je vydaný prostřednictvím NuGet v menších balíčcích sestavení. Místo jednoho velkého sestavení, které obsahuje většinu základních funkcí, je .NET Core dostupné jako menší balíčky zaměřené na funkce. Díky tomu je pro nás vhodnější model pro agilní vývoj a umožňuje optimalizovat aplikaci tak, aby zahrnovala jenom balíčky NuGet, které potřebujete. Výhody menšího povrchu aplikace zahrnují důkladné zabezpečení, omezenou údržbu, vyšší výkon a snížené náklady v modelu průběžných plateb.  
  
## <a name="the-net-core-platform"></a>Platforma .NET Core  
 Platforma .NET Core se skládá z několika komponent, které zahrnují spravované kompilátory, modul runtime, knihovny základních tříd a řadu modelů aplikací, například ASP.NET Core. Další informace o různých součástech a o tom, jak se zabývají, najdete v následujících úložištích [GitHub](https://github.com/) :  
  
- [.NET Core](https://github.com/dotnet/core)  
  
- [CoreFX – základní knihovny pro .NET Core](https://github.com/dotnet/corefx)  
  
- [CoreCLR – modul runtime .NET Core](https://github.com/dotnet/coreclr)  
  
- [CLI – nástroje příkazového řádku .NET Core](https://github.com/dotnet/cli)  
  
- [Roslyn – .NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Viz také:

- [Kurz pro .NET – Hello World za 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Průvodce platformou .NET Core](../../core/index.md)
- [Dokumentace k ASP.NET Core](/aspnet/core/)
