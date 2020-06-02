---
title: Pokyny k používání
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 03eaba3e52cb25619f65637efb4f414c22770440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291341"
---
# <a name="usage-guidelines"></a>Pokyny k používání

Tato část obsahuje pokyny pro použití běžných typů ve veřejně přístupných rozhraních API. Zabývá se přímým využitím integrovaných typů rozhraní (např. atributy serializace) a přetížení běžných operátorů.
  
<xref:System.IDisposable?displayProperty=nameWithType>Toto rozhraní se v této části nezabývá, ale je popsané v části [vzor Dispose](../garbage-collection/implementing-dispose.md) .

> [!NOTE]
> Pokyny a další informace o dalších běžných integrovaných typech .NET Framework najdete v referenčních tématech následujících: <xref:System.DateTime?displayProperty=nameWithType> , <xref:System.DateTimeOffset?displayProperty=nameWithType> , <xref:System.ICloneable?displayProperty=nameWithType> , <xref:System.IComparable%601?displayProperty=nameWithType> , <xref:System.IEquatable%601?displayProperty=nameWithType> , <xref:System.Nullable%601?displayProperty=nameWithType> , <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> .

## <a name="in-this-section"></a>V této části

[Pole](arrays.md)  
[Atributy](attributes.md)  
[Kolekce](guidelines-for-collections.md)  
[Serializace](serialization.md)  
[Použití System. XML](system-xml-usage.md)  
[Operátory rovnosti](equality-operators.md)  

*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*
  
## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
