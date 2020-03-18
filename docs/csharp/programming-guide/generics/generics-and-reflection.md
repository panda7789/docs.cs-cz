---
title: Obecné typy a reflexe – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 4893bf5ebe73988bb6535cc2a85591ff0dde6ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712166"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Obecné typy a reflexe (Průvodce programováním v C#)
Vzhledem k tomu, že clr (Common Language Runtime) má přístup k obecným informacím o typu za běhu, můžete použít reflexe k získání informací o obecných typech stejným způsobem jako u neobecných typů. Další informace naleznete [v tématu Obecné typy v době spuštění](./generics-in-the-run-time.md).  
  
 V rozhraní .NET Framework 2.0 několik nových <xref:System.Type> členů jsou přidány do třídy povolit informace za běhu pro obecné typy. Další informace o použití těchto metod a vlastností naleznete v dokumentaci k těmto třídám. Obor <xref:System.Reflection.Emit> názvů také obsahuje nové členy, které podporují obecné typy. Viz [Postup: Definování obecného typu s odrazem emit](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Seznam podmínek invariantní pro termíny používané v <xref:System.Type.IsGenericType%2A> obecné reflexe naleznete v poznámkách vlastnosti.  
  
|Název člena system.type|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Vrátí hodnotu true, pokud je typ obecný.|  
|<xref:System.Type.GetGenericArguments%2A>|Vrátí pole `Type` objektů, které představují argumenty typu zadané pro vytvořený typ nebo parametry typu definice obecného typu.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Vrátí základní definici obecného typu pro aktuální konstruovaný typ.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Vrátí pole `Type` objektů, které představují omezení aktuálního parametru obecného typu.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Vrátí hodnotu true, pokud typ nebo některý z jeho ohraničujících typů nebo metod obsahuje parametry typu, pro které nebyly zadány určité typy.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Získá kombinaci `GenericParameterAttributes` příznaků, které popisují zvláštní omezení aktuální ho obecného typu parametru.|  
|<xref:System.Type.GenericParameterPosition%2A>|Pro `Type` objekt, který představuje parametr typu, získá pozici parametru typu v seznamu parametrů typu definice obecného typu nebo definice obecné metody, která deklarovala parametr typu.|  
|<xref:System.Type.IsGenericParameter%2A>|Získá hodnotu, která `Type` označuje, zda aktuální představuje parametr typu obecného typu nebo definice metody.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Získá hodnotu, která <xref:System.Type> označuje, zda aktuální představuje definici obecného typu, ze kterého lze sestavit jiné obecné typy. Vrátí hodnotu true, pokud typ představuje definici obecného typu.|  
|<xref:System.Type.DeclaringMethod%2A>|Vrátí obecnou metodu, která definovala aktuální parametr obecného typu, nebo hodnotu null, pokud parametr typu nebyl definován obecnou metodou.|  
|<xref:System.Type.MakeGenericType%2A>|Nahradí prvky pole typů parametry typu aktuální definice obecného typu a <xref:System.Type> vrátí objekt představující výsledný konstruovaný typ.|  
  
 Kromě toho členové <xref:System.Reflection.MethodInfo> třídy povolit informace za běhu pro obecné metody. <xref:System.Reflection.MethodBase.IsGenericMethod%2A> Viz vlastnost poznámky pro seznam podmínek invariantní pro termíny používané k reflexi na obecné metody.  
  
|Název člena System.Reflection.MemberInfo|Popis|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Vrátí hodnotu true, pokud je metoda obecná.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Vrátí pole Type objekty, které představují argumenty typu vyrobenou obecnou metodu nebo parametry typu definice obecné metody.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Vrátí základní definici obecné metody pro aktuální vyrobenou metodu.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Vrátí hodnotu true, pokud metoda nebo některý z jejích ohraničujících typů obsahují parametry typu, pro které nebyly zadány určité typy.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Vrátí hodnotu <xref:System.Reflection.MethodInfo> true, pokud aktuální představuje definici obecné metody.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Nahradí prvky pole typů parametry typu aktuální definice obecné metody a <xref:System.Reflection.MethodInfo> vrátí objekt představující výslednou vyrobenou metodu.|  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Obecné typy](./index.md)
- [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Obecné typy](../../../standard/generics/index.md)
