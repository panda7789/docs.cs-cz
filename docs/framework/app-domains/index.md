---
title: Programování s doménami aplikací a sestaveními
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 2c849d27c70971d17bf4359ee7ae1081ee976a5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73119822"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programování s doménami aplikací a sestaveními

Hostitelé, jako je microsoft internet explorer, ASP.NET a prostředí systému Windows, načítají za běhu společného jazyka do procesu, vytvářejí v tomto procesu [doménu aplikace](application-domains.md) a při spuštění aplikace rozhraní .NET Framework načítají a spouštějí uživatelský kód v této doméně aplikace. Ve většině případů se nemusíte starat o vytváření aplikačních domén a načítání sestavení do nich, protože hostitel runtime provádí tyto úlohy.  
  
Pokud však vytváříte aplikaci, která bude hostitelem běžného jazykového běhu, vytváříte nástroje nebo kód, který chcete programově uvolnit, nebo vytváříte připojitelné součásti, které lze uvolnit a znovu načíst za běhu, budete vytvářet vlastní aplikačních domén. I v případě, že nevytváříte hostitele runtime, tato část obsahuje důležité informace o tom, jak pracovat s aplikačními doménami a sestaveními načtenými v těchto aplikačních doménách.  
  
## <a name="in-this-section"></a>V tomto oddílu  

[Témata s návody k doménám a sestavením aplikací](application-domains-and-assemblies-how-to-topics.md)  
Obsahuje odkazy na všechna témata s postupy, která naleznete v koncepční dokumentaci pro programování s aplikačními doménami a sestaveními.  
  
[Používání domén aplikací](use.md)  
Obsahuje příklady vytváření, konfigurace a používání aplikačních domén.  
  
[Programování se sestaveními](../../standard/assembly/program.md)  
Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.  
  
## <a name="related-sections"></a>Související oddíly  

[Generování dynamických metod a sestavení](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
Popisuje způsob vytváření dynamických sestavení.  
  
[Sestavení v .NET](../../standard/assembly/index.md)  
Poskytuje koncepční přehled sestavení.  
  
[Aplikační domény](application-domains.md)  
Poskytuje koncepční přehled domén aplikací.  
  
[Přehled reflexe](../reflection-and-codedom/reflection.md)  
Popisuje, jak použít **Reflection** třídy získat informace o sestavení.
