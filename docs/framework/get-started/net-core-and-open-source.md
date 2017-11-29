---
title: .NET Core a open source
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8233db6bdf8c07bcc62f2e0f3819afb72dc10f5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="net-core-and-open-source"></a>.NET Core a open source
Toto téma obsahuje stručný přehled co .NET Core a ukazuje, jak můžete najít další informace. Úplný seznam témat pro .NET Core naleznete [.NET Core průvodce](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>Co je .NET Core?  
 .NET core je obecné účely, modulární, napříč platformami a open source implementace .NET Standard. Obsahuje řadu stejná rozhraní API jako rozhraní .NET Framework (ale .NET Core je menší sadu) a zahrnuje modul runtime, framework, kompilátoru a nástroje pro součásti, které podporují celou řadu operačních systémů a čip cíle. Implementace .NET Core se primárně vycházejí úlohami ASP.NET Core, ale také potřeba a chcete mít více moderní implementace. Je můžete použít v zařízení, cloudu a scénáře vložených/IoT.  
  
 Chcete-li začít pracovat s .NET Core, navštivte [domovské stránky .NET Core](https://www.microsoft.com/net/core).  
  
 Zde jsou hlavní vlastnosti .NET Core:  
  
-   **Napříč platformami:** .NET Core poskytuje klíčové funkce pro implementaci funkce aplikací, které potřebujete a znovu použít tento kód bez ohledu na vaše cílové platformy. Aktuálně podporuje tři hlavní operační systémy (OS): Windows, Linux a systému macOS. Můžete napsat aplikace a knihovny, které běží ve podporované operační systémy beze změny. Chcete-li zobrazit seznam podporovaných operačních systémů, navštivte [.NET Core plán](https://github.com/dotnet/core/blob/master/roadmap.md).
  
-   **S otevřeným zdrojem:** .NET Core je jednou z mnoha projektů v části péči o [.NET Foundation](http://www.dotnetfoundation.org/) a je k dispozici na [Githubu](https://github.com/).  S .NET Core jako opensourcový projekt podporuje více transparentní procesu vývoje a zvýší úroveň aktivní a aktivnější komunity.  
  
-   **Flexibilní nasazení:** existují dva hlavní způsoby k nasazení své aplikace: samostatná nasazení nebo nasazení framework závislé. Nasazení závislé na framework jsou nainstalované jenom svoje závislosti aplikace a třetích stran a aplikace závisí na systémové verzi .NET Core nacházet.  Samostatná nasazení verze .NET Core sloužící k vytvoření aplikace je nasazená taky společně s vaší aplikace a třetích stran závislosti a lze spustit souběžně sdílená s jinými verzemi.    Další informace najdete v tématu [nasazení aplikace .NET Core](../../core/deploying/index.md).

-   **Modulární:** .NET Core je modulární, protože bylo vydáno prostřednictvím balíčku NuGet v rámci menší balíčky sestavení. Místo jeden velký sestavení, které obsahuje většinu základní funkce je k dispozici jako menší balíčky zaměřené na funkce .NET Core. To umožňuje více agilní model vývoje pro nás a umožňuje optimalizovat aplikaci, kterou chcete zahrnout jenom balíčky NuGet, které potřebujete. Příklady výhod menší aplikace útoku spolehlivější zabezpečení snížit údržby, zvýšení výkonu a snížení nákladů ve model platím pro what--používání.  
  
## <a name="the-net-core-platform"></a>Možnosti základní platformy .NET  
 Platformy .NET Core přišla několik komponent, která zahrnuje spravované kompilátory, modulu runtime, knihovny základní třídy a množství modely aplikace, jako je ASP.NET Core. Další informace o různých komponent a získat zapojení, navštivte následující [Githubu](https://github.com/) úložiště:  
  
-   [.NET Core](https://github.com/dotnet/core)  
  
-   [CoreFX – základní knihovny .NET Core](https://github.com/dotnet/corefx)  
  
-   [CoreCLR - .NET Core runtime](https://github.com/dotnet/coreclr)  
  
-   [Rozhraní příkazového řádku - nástroje příkazového řádku .NET Core](https://github.com/dotnet/cli)  
  
-   [Roslyn - kompilátoru platformy .NET](https://github.com/dotnet/roslyn)  
  
-   [Jádro ASP.NET](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Viz také  
 [.NET core domovské stránky](https://www.microsoft.com/net/core)  
 [Příručka pro základní rozhraní .NET](../../core/index.md)  
 [Dokumentace k technologii ASP.NET](/aspnet/core/)
