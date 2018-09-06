---
title: 'Postupy: vytváření sjednocení C / C++ pomocí atributů (C#)'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 8b5a88656b1172407c3e5b9f5198d5acae7bf9e0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798506"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Postupy: vytváření sjednocení C/C++ pomocí atributů (C#)
Pomocí atributů můžete přizpůsobit, jak jsou rozloženy struktury v paměti. Například můžete vytvořit, která se označuje jako sjednocení v jazyce C/C++ pomocí `StructLayout(LayoutKind.Explicit)` a `FieldOffset` atributy.  
  
## <a name="example"></a>Příklad  
 V tomto segmentu kódu, všechna pole z `TestUnion` začínají na stejné místo v paměti.  
  
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
 Tady je další příklad – kde pole začínají na různých explicitně nastavit umístění.  
  
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
  
 Dvě celočíselné pole, `i1` a `i2`, sdílet stejné umístění paměti jako `lg`. Tento typ kontroly nad rozložení struktury je užitečné při použití vyvolání platformy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection>  
- <xref:System.Attribute>  
- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
- [Atributy](../../../../../docs/standard/attributes/index.md)  
- [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
- [Atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [Vytváření vlastních atributů (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
- [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
