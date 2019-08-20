---
title: 'Postupy: VytvořeníC++ sjednocení jazyka C pomocí atributů (C#)'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: fdadc9505b93f40c66001ac36345efada2edd270
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595369"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Postupy: Vytvoření C/C++ sjednocení pomocí atributů (C#)
Pomocí atributů můžete přizpůsobit způsob, jakým jsou struktury rozloženy v paměti. Můžete například vytvořit, co se říká sjednocení v C/C++ `StructLayout(LayoutKind.Explicit)` pomocí atributů a. `FieldOffset`  
  
## <a name="example"></a>Příklad  
 V tomto segmentu kódu všechna pole `TestUnion` začínají ve stejném umístění v paměti.  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestUnion  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public byte b;  
       }  
```  
  
## <a name="example"></a>Příklad  
 Následuje další příklad, kdy se pole spouštějí v různých explicitních nastaveních umístění.  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestExplicit  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public long lg;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i1;  
  
           [System.Runtime.InteropServices.FieldOffset(4)]  
           public int i2;  
  
           [System.Runtime.InteropServices.FieldOffset(8)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(12)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(14)]  
           public byte b;  
       }  
```  
  
 Dvě celočíselná pole `i1` a `i2`sdílejí stejná umístění v paměti jako `lg`. Tento druh řízení nad rozložením struktury je užitečný při volání platformy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním v jazyce C#](../../index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy (C#)](./index.md)
- [Vytváření vlastních atributů (C#)](./creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (C#)](./accessing-attributes-by-using-reflection.md)
