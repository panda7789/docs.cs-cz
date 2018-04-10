---
title: Obecné typy a reflexe (Průvodce programováním v C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3048cb6a9b333107f6ea37edf31ead96f9fe2057
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="generics-and-reflection-c-programming-guide"></a>Obecné typy a reflexe (Průvodce programováním v C#)
Protože Common Language Runtime (CLR) má přístup k informacím obecného typu za běhu, můžete získat informace o obecné typy v stejným způsobem jako u neobecné typy reflexe. Další informace najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 V [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] několik nových členů jsou přidány do <xref:System.Type> třída povolit informace o běhu pro obecné typy. Na další informace o tom, jak používat tyto metody a vlastnosti těchto tříd naleznete v dokumentaci. <xref:System.Reflection.Emit> Obor názvů obsahuje také nové členy, které podporují obecné typy. V tématu [postupy: definování obecného typu pomocí reflexe emitování](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Seznam termínů používaných v obecné reflexe invariantní podmínek, najdete v tématu <xref:System.Type.IsGenericType%2A> vlastnost poznámky.  
  
|Název člena System.Type|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Vrátí hodnotu true Pokud je obecného typu.|  
|<xref:System.Type.GetGenericArguments%2A>|Vrátí pole `Type` objekty, které představují argumenty typu zadaná pro vytvořený typu nebo typu parametry definice obecného typu.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Vrátí základní definice obecného typu pro aktuální typ vytvořený.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Vrátí pole `Type` objekty, které představují omezení u aktuální obecný parametr typu.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Vrátí hodnotu true Pokud je typ nebo některé z nadřazených typů a metod obsahovat parametry typu, pro které nebyla zadána konkrétní typy.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Získá kombinaci `GenericParameterAttributes` příznaky, které popisují speciální omezení aktuální obecný parametr typu.|  
|<xref:System.Type.GenericParameterPosition%2A>|Pro `Type` objekt, který reprezentuje parametr typu získá pozici parametr typu v seznamu parametrů typu definice obecného typu nebo definici obecná metoda, která deklarovaný parametr typu.|  
|<xref:System.Type.IsGenericParameter%2A>|Získá hodnotu, která určuje, zda aktuální `Type` představuje parametr typu obecný typ nebo metoda definice.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Získá hodnotu, která určuje, zda aktuální <xref:System.Type> představuje definice obecného typu, ze kterého lze sestavit další obecné typy. Vrátí hodnotu true Pokud typ představuje definici obecného typu.|  
|<xref:System.Type.DeclaringMethod%2A>|Vrací obecná metoda, která definována aktuální obecná typ parametru, nebo hodnota null, pokud parametr typu nebyl definované obecná metoda.|  
|<xref:System.Type.MakeGenericType%2A>|Nahradí prvků pole typy parametrů typu aktuální definice obecného typu a vrátí <xref:System.Type> objekt reprezentující výsledná sestavený typu.|  
  
 Kromě toho členy <xref:System.Reflection.MethodInfo> třída povolit informace o běhu pro obecné metody. Najdete v článku <xref:System.Reflection.MethodBase.IsGenericMethod%2A> vlastnost poznámky seznam invariantní podmínky pro termínů používaných, aby odpovídala v obecné metody.  
  
|Název člena System.Reflection.MemberInfo|Popis|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Vrátí hodnotu true Pokud je obecná metoda.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Vrátí pole Typ objektů, které představují argumenty typu sestavené obecné metody nebo parametry typu definice obecná metoda.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Vrátí základní definice obecné metody pro aktuální metoda vytvořený.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Vrátí hodnotu true Pokud metoda nebo některý z jeho nadřazených typů obsahovat všechny parametry typu, pro které nebyla zadána konkrétní typy.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Vrátí hodnotu true, pokud aktuální <xref:System.Reflection.MethodInfo> představuje definici obecná metoda.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Nahradí prvků pole typy parametrů typu aktuální definice obecné metody a vrátí <xref:System.Reflection.MethodInfo> objekt reprezentující výsledná sestavený metoda.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
 [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [Obecné typy](~/docs/standard/generics/index.md)
