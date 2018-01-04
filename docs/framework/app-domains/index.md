---
title: "Programování s doménami aplikací a sestaveními"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 216766a8d8f120594c7d6dd1fd192f90b775c1d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programování s doménami aplikací a sestaveními
Vytvořte hostitele, jako je například aplikace Microsoft Internet Explorer, ASP.NET a načtení prostředí Windows modul common language runtime do procesu, [domény aplikace](../../../docs/framework/app-domains/application-domains.md) v tom, že zpracování a pak můžete načíst a spuštění uživatelského kódu v této doméně Při spuštění aplikace rozhraní .NET Framework. Ve většině případů nemáte starosti vytvoření domény aplikace a načtení sestavení do nich, protože hostitel běhu provádí tyto úlohy.  
  
 Ale při vytváření aplikace, která bude hostitelem modul CLR, vytvořit nástroje nebo kód, který chcete uvolnit prostřednictvím kódu programu, nebo vytvořit modulární součásti, které mohou být uvolněny nebo za chodu, bude vytvářet vlastní aplikační domény. I když nejsou vytvoření hostitele modulu runtime, tato část obsahuje důležité informace o tom, jak pracovat s doménami aplikací a sestaveními načíst v těchto doménách aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Témata s návody k doménám a sestavením aplikací](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 Obsahuje odkazy na všechny postupy v rámcová dokumentace k programování s doménami aplikací a sestaveními.  
  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)  
 Obsahuje příklady vytvoření, konfiguraci a používání domén aplikací.  
  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Popisuje způsob vytváření dynamických sestavení.  
  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Poskytuje koncepční přehled sestavení.  
  
 [Aplikační domény](../../../docs/framework/app-domains/application-domains.md)  
 Poskytuje koncepční přehled domén aplikací.  
  
 [Přehled reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Popisuje postup použití **reflexe** třída získat informace o sestavení.
