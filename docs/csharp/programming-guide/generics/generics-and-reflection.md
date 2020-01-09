---
title: Obecné typy a reflexe – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 4893bf5ebe73988bb6535cc2a85591ff0dde6ebd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712166"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Obecné typy a reflexe (Průvodce programováním v C#)
Vzhledem k tomu, že modul CLR (Common Language Runtime) má přístup k informacím o obecném typu za běhu, můžete pomocí reflexe získat informace o obecných typech stejným způsobem jako u neobecných typů. Další informace naleznete v tématu [Obecné typy v době běhu](./generics-in-the-run-time.md).  
  
 V .NET Framework 2,0 jsou do třídy <xref:System.Type> přidány několik nových členů, aby byly pro obecné typy povoleny běhové informace. Další informace o tom, jak tyto metody a vlastnosti používat, najdete v dokumentaci k těmto třídám. Obor názvů <xref:System.Reflection.Emit> obsahuje také nové členy, které podporují obecné typy. Viz [Postupy: definování obecného typu pomocí generování reflexe](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Seznam neutrálních podmínek pro výrazy používané v obecném reflexi naleznete v tématu <xref:System.Type.IsGenericType%2A> vlastnosti poznámky.  
  
|Název člena System. Type|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Vrátí hodnotu true, pokud je typ obecný.|  
|<xref:System.Type.GetGenericArguments%2A>|Vrátí pole objektů `Type`, které reprezentují argumenty typu zadané pro konstruovaný typ, nebo parametry typu definice obecného typu.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Vrátí základní definici obecného typu pro aktuální konstruovaný typ.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Vrátí pole objektů `Type`, které reprezentují omezení na aktuálním parametru obecného typu.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Vrátí hodnotu true, pokud typ nebo některý z jeho nadřazených typů nebo metod obsahuje parametry typu, pro které nebyly zadány konkrétní typy.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Získá kombinaci příznaků `GenericParameterAttributes`, které popisují zvláštní omezení aktuálního parametru obecného typu.|  
|<xref:System.Type.GenericParameterPosition%2A>|Pro objekt `Type`, který představuje parametr typu, získá pozici parametru typu v seznamu parametrů typu definice obecného typu nebo definice obecné metody, která je deklarována jako parametr typu.|  
|<xref:System.Type.IsGenericParameter%2A>|Získá hodnotu, která označuje, zda aktuální `Type` představuje parametr typu obecného typu nebo definice metody.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Získá hodnotu, která označuje, zda aktuální <xref:System.Type> představuje definici obecného typu, ze které lze sestavit další obecné typy. Vrátí hodnotu true, pokud typ představuje definici obecného typu.|  
|<xref:System.Type.DeclaringMethod%2A>|Vrátí obecnou metodu, která definovala aktuální parametr obecného typu, nebo hodnotu null, pokud parametr typu nebyl definován obecnou metodou.|  
|<xref:System.Type.MakeGenericType%2A>|Nahradí prvky pole typů pro parametry typu aktuální definice obecného typu a vrátí objekt <xref:System.Type> reprezentující výsledný konstruovaný typ.|  
  
 Kromě toho členové třídy <xref:System.Reflection.MethodInfo> povolují běhové informace pro obecné metody. V tématu <xref:System.Reflection.MethodBase.IsGenericMethod%2A> vlastnost poznámky naleznete seznam neutrálních podmínek pro výrazy použité k reflexi u obecných metod.  
  
|Název člena System. Reflection. MemberInfo|Popis|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Vrátí hodnotu true, pokud je metoda obecná.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Vrátí pole typů objektů, které reprezentují argumenty typu konstruované obecné metody nebo parametry typu definice obecné metody.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Vrátí základní definici obecné metody pro aktuální vytvořenou metodu.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Vrátí hodnotu true, pokud metoda nebo některý z jejích nadřazených typů obsahuje všechny parametry typu, pro které nebyly zadány konkrétní typy.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Vrátí hodnotu true, pokud aktuální <xref:System.Reflection.MethodInfo> představuje definici obecné metody.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Nahradí prvky pole typů pro parametry typu aktuální definice obecné metody a vrátí objekt <xref:System.Reflection.MethodInfo> reprezentující výslednou vytvořenou metodu.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Obecné typy](./index.md)
- [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Obecné typy](../../../standard/generics/index.md)
