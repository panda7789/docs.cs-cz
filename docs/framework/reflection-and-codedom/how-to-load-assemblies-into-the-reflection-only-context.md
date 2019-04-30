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
ms.openlocfilehash: 8dc05d27b0316c82c5314a766fcad929dc5f3698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793130"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Postupy: Načtení sestavení do kontextu pouze pro reflexi
Kontext načítání pouze pro reflexi umožňuje zkoumat sestavení zkompilován pro jiné platformy nebo u jiných verzí rozhraní .NET Framework. Jenom se dají prozkoumat kód načtený do tohoto kontextu; nelze provést. To znamená, že nelze vytvořit objekty, protože konstruktory nemůže být proveden. Protože kód nelze provést, nejsou automaticky nahrány závislosti. Pokud je potřeba je prozkoumat, je nutné načíst je sami.  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Načtení sestavení do kontextu pouze pro reflexi zatížení  
  
1. Použití <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> přetížení metody se načíst sestavení zadané zobrazované jméno, nebo <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodu pro načtení sestavení zadané cestě. Pokud je sestavení binárního obrazu, použijte <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> přetížení metody.  
  
    > [!NOTE]
    >  Načíst verzi souboru mscorlib.dll z verze rozhraní .NET Framework než verze v kontextu spuštění nelze použít kontext pouze pro reflexi.  
  
2. Pokud sestavení obsahuje závislosti, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> je metoda nenačte. Pokud je potřeba je prozkoumat, je nutné načíst je sami.  
  
3. Určení, zda je sestavení načteno do kontextu pouze pro reflexi pomocí sestavení <xref:System.Reflection.Assembly.ReflectionOnly%2A> vlastnost.  
  
4. Pokud se atributy se použily k sestavení a typy v sestavení, prozkoumejte tyto atributy s použitím <xref:System.Reflection.CustomAttributeData> třídu zajistíte, že je proveden žádný pokus o spouštění kódu v kontextu pouze pro reflexi. Použijte odpovídající přetížení <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metodu k získání <xref:System.Reflection.CustomAttributeData> reprezentují atributy použité na sestavení, člen, modul nebo parametr.  
  
    > [!NOTE]
    >  Atributy použité na sestavení nebo k jejímu obsahu může být definované v sestavení nebo mohou být definovány v jiném sestavení načtena do kontextu pouze pro reflexi. Neexistuje žádný způsob, jak předem říct, kde jsou definovány atributy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak prozkoumat atributy použité u sestavení načtena do kontextu pouze pro reflexi.  
  
 Příklad kódu definuje vlastní atribut s dva konstruktory a jednu vlastnost. Atribut je použit k sestavení, typ deklarovaný v sestavení, metoda typu a parametru metody. Při spuštění sestavení samotné načte do kontextu pouze pro reflexi a zobrazí informace o vlastních atributů, které byly použity k němu a k typům a členům, které obsahuje.  
  
> [!NOTE]
>  Pro zjednodušení příkladu kódu, sestavení načte a zkoumá samotný. Za normálních okolností by měli očekávat najít stejné sestavení načtena do kontextu spuštění a kontextu pouze pro reflexi.  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
