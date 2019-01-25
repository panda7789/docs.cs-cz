---
title: .NET Core a open source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3c48182ab5a864228fd1d2ccf32d714ebccf60a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494558"
---
# <a name="net-core-and-open-source"></a>.NET Core a open source
Toto téma nabízí stručný přehled o co .NET Core se a ukazuje, jak můžete najít další informace. Úplný seznam témat pro .NET Core, najdete v tématu [Průvodce platformou .NET Core](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>Co je .NET Core?  
 .NET core je obecný, modulární, napříč platformami a open source implementace .NET Standard. Obsahuje řadu stejných rozhraní API jako rozhraní .NET Framework (ale .NET Core je sada menší) a zahrnuje modul runtime, rozhraní, kompilátor a nástroje součásti, které podporují širokou škálu operačních systémů a čip cíle. Implementace .NET Core se primárně řízené úlohy ASP.NET Core, ale také podle potřeby a chcete mít více moderní implementaci. Je možné v zařízení a cloudové aplikace a scénáře vložené a IoT.  
  
 Chcete-li začít pracovat s .NET Core, navštivte prosím [domovské stránky .NET Core](https://www.microsoft.com/net/core).  
  
 Tady jsou hlavní vlastnosti rozhraní .NET Core:  
  
-   **Různé platformy:** poskytuje klíčové funkce, které implementují funkce aplikací, které potřebujete a znovu použít tento kód bez ohledu na cílové platformy .NET Core. Aktuálně podporuje tři hlavní operační systémy (OS): Windows, Linux a macOS. Můžete napsat aplikací a knihoven, které poběží bez úprav na podporovaných operačních systémů. Chcete-li zobrazit seznam podporovaných operačních systémů, navštivte [.NET Core – plán](https://github.com/dotnet/core/blob/master/roadmap.md).
  
-   **Otevřít zdroj:** .NET Core je jednou z mnoha projektů v rámci péči o [.NET Foundation](https://www.dotnetfoundation.org/) a je k dispozici na [Githubu](https://github.com/).  S .NET Core jako opensourcový projekt podporuje transparentnější proces vývoje a podporuje aktivní a aktivní komunitou.  
  
-   **Flexibilní nasazení:** existují dva hlavní způsoby, jak nasazení vaší aplikace: samostatná nasazení nebo nasazení závisí na architektuře. S nasazením závisí na architektuře pouze závislostí třetích stran a aplikace jsou nainstalované a vaše aplikace závisí na verzi .NET Core nacházet celý systém.  Samostatná nasazení verzi .NET Core sloužící k sestavení aplikace nasazuje spolu s vaší aplikace a třetích stran závislosti a lze spustit vedle sebe s jinými verzemi.    Další informace najdete v tématu [nasazení aplikace .NET Core](../../core/deploying/index.md).

-   **Modulární:** .NET Core je modulární, protože je vydané prostřednictvím balíčku NuGet v menší balíčky sestavení. Místo jedno velké sestavení, která obsahuje většinu funkcí core .NET Core je k dispozici jako menší balíčky zaměřené na funkce. Díky tomu agilnější model vývoje nám a umožňuje optimalizovat aplikaci a zahrnout jen ty balíčky, které potřebujete. Výhodám menší plochy oblast aplikace patří důkladnější zabezpečení snížit údržby, vyšší výkon a snížit náklady v modelu plateb pro what využití.  
  
## <a name="the-net-core-platform"></a>Na platformě .NET Core  
 Platformy .NET Core se provádí několik komponent, který obsahuje spravované kompilátory, modul runtime, knihovny základních tříd a mnoho aplikačních modelů, jako je ASP.NET Core. Další informace o různých komponentách a získat zapojení, navštivte následující [Githubu](https://github.com/) úložišť:  
  
-   [.NET Core](https://github.com/dotnet/core)  
  
-   [CoreFX – základní knihovny .NET Core](https://github.com/dotnet/corefx)  
  
-   [CoreCLR - .NET Core runtime](https://github.com/dotnet/coreclr)  
  
-   [Rozhraní příkazového řádku – nástroje příkazového řádku .NET Core](https://github.com/dotnet/cli)  
  
-   [Roslyn - .NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
-   [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Viz také:
- [Domovská stránka .NET core](https://www.microsoft.com/net/core)
- [Průvodce platformou .NET Core](../../core/index.md)
- [Dokumentace k ASP.NET Core](/aspnet/core/)
