---
title: 'Postupy: Načtení sestavení do kontextu pouze pro reflexi'
description: Podívejte se na příklad načtení sestavení do kontextu pouze pro reflexi v rozhraní .NET. Prověřte sestavení kompilovaná pro jiné platformy nebo verze rozhraní .NET.
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
ms.openlocfilehash: 92f847f6c61ba39bf8621af6080baccfdabe514a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865070"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Postupy: Načtení sestavení do kontextu pouze pro reflexi

Kontext zatížení pouze pro reflexi umožňuje kontrolovat sestavení kompilovaná pro jiné platformy nebo pro jiné verze .NET Framework. Kód načtený do tohoto kontextu lze prozkoumat pouze; nedá se spustit. To znamená, že objekty nelze vytvořit, protože nelze provést konstruktory. Vzhledem k tomu, že kód nelze provést, závislosti nejsou automaticky načteny. Pokud je potřebujete ověřit, musíte je načíst sami.

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Načtení sestavení do kontextu načtení pouze pro reflexi

1. <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29>K načtení sestavení podle jeho zobrazovaného názvu použijte přetížení metody, nebo <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodu pro načtení sestavení, které danou cestu zadala. Pokud je sestavení binární image, použijte <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> přetížení metody.

    > [!NOTE]
    > Kontext pouze pro reflexi nelze použít k načtení verze mscorlib.dll z verze .NET Framework jiné než verze v kontextu spuštění.

2. Pokud sestavení obsahuje závislosti, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Metoda je nenačte. Pokud je potřebujete ověřit, musíte je načíst sami.

3. Určete, zda je sestavení načteno do kontextu pouze pro reflexi pomocí vlastnosti sestavení <xref:System.Reflection.Assembly.ReflectionOnly%2A> .

4. Pokud byly atributy použity na sestavení nebo na typy v sestavení, zkontrolujte tyto atributy pomocí třídy, aby se <xref:System.Reflection.CustomAttributeData> zajistilo, že není proveden žádný pokus o spuštění kódu v kontextu pouze pro reflexi. Použijte příslušné přetížení <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody pro získání <xref:System.Reflection.CustomAttributeData> objektů představujících atributy použité pro sestavení, člena, modul nebo parametr.

    > [!NOTE]
    > Atributy použité pro sestavení nebo jejich obsah mohou být definovány v sestavení nebo mohou být definovány v jiném sestavení načteno do kontextu pouze pro reflexi. Neexistuje žádný způsob, jak sdělit předem, kde jsou definovány atributy.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak ověřit atributy použité pro sestavení načtené do kontextu pouze pro reflexi.

Příklad kódu definuje vlastní atribut se dvěma konstruktory a jednou vlastností. Atribut se aplikuje na sestavení, na typ deklarovaný v sestavení, na metodu typu a na parametr metody. Po spuštění sestavení se načte do kontextu pouze pro reflexi a zobrazí informace o vlastních atributech, které byly na něj aplikovány, a o typech a členech, které obsahuje.

> [!NOTE]
> Pro zjednodušení příkladu kódu sestavení načítá a kontroluje sám sebe. Za normálních okolností neočekáváte, aby bylo stejné sestavení načteno do kontextu spuštění i kontextu pouze pro reflexi.

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
