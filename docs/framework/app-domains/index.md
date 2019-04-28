---
title: Programování s doménami aplikací a sestaveními
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7124b6b234601e3afc27109ac318f47e3fe40c35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675348"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programování s doménami aplikací a sestaveními
Vytvoření hostitele, jako je Microsoft Internet Explorer, ASP.NET a načtení Windows prostředí common language runtime do procesu, [aplikační domény](../../../docs/framework/app-domains/application-domains.md) v dané zpracování a pak načíst a spustit uživatelský kód v této doméně aplikace Při spuštění aplikace rozhraní .NET Framework. Ve většině případů není nutné se starat o vytváření domény aplikace a načítání sestavení do nich, protože hostitelský modul runtime provádí tyto úlohy.  
  
 Nicméně pokud vytváříte aplikaci, která bude hostovat modul common language runtime, vytvořit nástroje nebo kódu, které chcete uvolnit prostřednictvím kódu programu, nebo vytvořit modulární komponenty, které mohou být a projekt znovu nenačtete v reálném čase, budete vytvářet vlastní aplikační domény. I když nejsou vytvořit hostitelský modul runtime, tato část obsahuje důležité informace o tom, jak pracovat s doménami aplikací a sestavení načtená v těchto doménách aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Témata s návody k doménám a sestavením aplikací](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 Obsahuje odkazy na všechny postupy v rámcové dokumentaci k programování s doménami aplikací a sestaveními.  
  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)  
 Obsahuje příklady vytváření, konfiguraci a používání domén aplikací.  
  
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
 Popisuje způsob použití **reflexe** třídy k získání informací o sestavení.
