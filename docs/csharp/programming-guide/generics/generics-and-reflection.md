---
title: Obecné typy a reflexe - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 6a014309829d7dbd477a7ae4a658b84a3f35d91f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742416"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Obecné typy a reflexe (Průvodce programováním v C#)
Protože Common Language Runtime (CLR) má přístup k informacím o obecného typu v době běhu, můžete získat informace o obecných typů v stejným způsobem jako u neobecné typy reflexe. Další informace najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 V [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] několik nových členů jsou přidány do <xref:System.Type> třídy umožňující běhových informací pro obecné typy. Další informace o tom, jak používat tyto metody a vlastnosti těchto tříd naleznete v dokumentaci. <xref:System.Reflection.Emit> Obor názvů obsahuje také nové členy, které podporují obecných typů. Zobrazit [jak: Definování obecného typu pomocí reflexe generování](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Seznam neutrálních podmínek pro výrazy použité v obecné reflexi naleznete v tématu <xref:System.Type.IsGenericType%2A> vlastnosti.  
  
|Název člena System.Type|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Vrátí true, pokud je typ obecný.|  
|<xref:System.Type.GetGenericArguments%2A>|Vrátí pole `Type` objekty, které představují argumentů typu pro konstruovaný typ nebo typ zadané parametry v definici obecného typu.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Vrátí základní definici obecného typu pro aktuální konstruovaný typ.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Vrátí pole `Type` objekty, které představují omezení na aktuální obecný parametr typu.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Vrátí true, pokud typ nebo některý z jeho nadřazené typy nebo metody obsahovat parametry typu, pro které nebyla zadána konkrétních typů.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Získá kombinaci `GenericParameterAttributes` příznaky, které popisují zvláštní omezení aktuální obecný parametr typu.|  
|<xref:System.Type.GenericParameterPosition%2A>|Pro `Type` objekt, který reprezentuje parametr typu získá pozice parametru typu v seznamu parametrů typu definici obecného typu nebo definice obecné metody, která deklarována jako parametr typu.|  
|<xref:System.Type.IsGenericParameter%2A>|Získá hodnotu určující, zda aktuální `Type` reprezentuje parametr typu v definici obecného typu nebo metody.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Získá hodnotu určující, zda aktuální <xref:System.Type> představuje definici obecného typu, ze kterého lze zkonstruovat další obecné typy. Vrátí true, pokud typ představuje definici obecného typu.|  
|<xref:System.Type.DeclaringMethod%2A>|Vrátí obecnou metodu, která definována aktuálním obecný parametr typu, nebo hodnota null, pokud je parametr typu nebyl definován pomocí obecné metody.|  
|<xref:System.Type.MakeGenericType%2A>|Nahradí prvky pole typů pro parametry typu aktuální definice obecného typu a vrátí <xref:System.Type> představující výsledný konstruovaný typ objektu.|  
  
 Kromě toho členové <xref:System.Reflection.MethodInfo> třídy povolit běhových informací pro obecné metody. Zobrazit <xref:System.Reflection.MethodBase.IsGenericMethod%2A> vlastnost poznámky seznam neutrálních podmínek pro výrazy použité tak, aby odrážely na obecné metody.  
  
|Název člena System.Reflection.MemberInfo|Popis|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Vrátí true, pokud metoda je obecná.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Vrátí pole objektů typu, které představují typy argumentů konstruovanou obecnou metodu nebo parametry typu Obecné metody.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Vrátí základní definice obecné metody pro aktuální konstruovaný metodu.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Vrátí true, pokud metoda nebo některé typy jejího nadřazeného obsahovat žádné parametry typu, pro které nebyla zadána konkrétní typy.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Vrátí hodnotu true, pokud aktuální <xref:System.Reflection.MethodInfo> představuje definici obecné metody.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Nahradí prvky pole typů pro parametry typu aktuální definice obecné metody a vrátí <xref:System.Reflection.MethodInfo> objekt představující výsledný vytvořena metoda.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)
- [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Obecné typy](~/docs/standard/generics/index.md)
