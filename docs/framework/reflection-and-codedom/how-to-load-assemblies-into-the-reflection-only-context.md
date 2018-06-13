---
title: 'Postupy: Načtení sestavení do kontextu pouze pro reflexi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7aa7f8a158a851baf76455da685059f02c69cb6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398723"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Postupy: Načtení sestavení do kontextu pouze pro reflexi
Kontext načítání pouze pro reflexi umožňuje zkontrolovat sestavení zkompilovat pro jiné platformy, nebo pro jiné verze rozhraní .NET Framework. Kód načtený do tohoto kontextu mohou být hodnoceny pouze; nelze provést. To znamená, že objekty nelze vytvořit, protože konstruktory nelze provést. Protože kód nelze provést, nejsou automaticky načíst závislosti. Pokud potřebujete posoudit, je nutné načíst je sami.  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Načtení sestavení do kontextu pouze pro reflexi zatížení  
  
1.  Použití <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> přetížení metody se načíst sestavení zadaný zobrazovaný název, nebo <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metoda načíst sestavení zadané cesty. Pokud je sestavení binární bitovou kopii, použijte <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> přetížení metody.  
  
    > [!NOTE]
    >  Kontext pouze pro reflexi nelze použít k načtení verzi mscorlib.dll z verze rozhraní .NET Framework, než verze v kontextu spuštění.  
  
2.  Pokud má sestavení závislosti, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> metoda je nenačte. Pokud potřebujete posoudit, je nutné načíst je sami.  
  
3.  Určit, zda je sestavení do kontextu pouze pro reflexi načíst pomocí sestavení <xref:System.Reflection.Assembly.ReflectionOnly%2A> vlastnost.  
  
4.  Pokud atributy se používají k sestavení nebo typy v sestavení, zkontrolujte pomocí těchto atributů <xref:System.Reflection.CustomAttributeData> třída zajistit, že žádné pokusu o spuštění kódu v kontextu pouze pro reflexi. Použijte odpovídající přetížení <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metoda získat <xref:System.Reflection.CustomAttributeData> objekty, které představují atributy použité na sestavení, člen, modul nebo parametr.  
  
    > [!NOTE]
    >  Atributy použité na sestavení nebo na jeho obsah může být definovaná v sestavení, nebo může být definovaná v jiném sestavení do kontextu pouze pro reflexi načteno. Neexistuje žádný způsob, jak předem říct, kde jsou definovány atributy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak prozkoumat atributy použité k sestavení do kontextu pouze pro reflexi načteno.  
  
 Příklad kódu definuje vlastní atribut s dva konstruktory a jednu vlastnost. Atribut se použije na sestavení, typu deklarován v sestavení, metoda typu a do parametru metody. Po provedení sestavení načte samotné do kontextu pouze pro reflexi a zobrazí informace o vlastních atributů, které byly použity k němu a typy a členy, které obsahuje.  
  
> [!NOTE]
>  Pro zjednodušení příkladu kódu, sestavení načte a prověří sám sebe. Za normálních okolností by byste měli najít do stejného sestavení do kontextu spuštění a kontext pouze pro reflexi načteno.  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>  
 <xref:System.Reflection.CustomAttributeData>
