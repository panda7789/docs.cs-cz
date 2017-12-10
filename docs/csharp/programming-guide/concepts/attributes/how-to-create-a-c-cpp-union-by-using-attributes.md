---
title: "Postupy: vytváření sjednocení C-C++ pomocí atributů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e9274b585c2fecf53b94d94f9bdfdaf4a47f1041
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Postupy: vytváření sjednocení C/C++ pomocí atributů (C#)
Pomocí atributů můžete přizpůsobit, jak jsou rozloženy struktury v paměti. Například můžete vytvořit, která se označuje jako sjednocení v jazyce C/C++ pomocí `StructLayout(LayoutKind.Explicit)` a `FieldOffset` atributy.  
  
## <a name="example"></a>Příklad  
 V tomto segmentu kódu, všechna pole z `TestUnion` spustit ve stejném umístění v paměti.  
  
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
 Zde je další příklad kde počáteční pole v různých explicitně nastavit umístění.  
  
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
  
 Pole dva celé číslo `i1` a `i2`, sdílet stejné umístění paměti jako `lg`. Tento druh kontrolu nad struktura rozložení je užitečné při použití vyvolání platformy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Průvodce programováním v C#](../../../../csharp/programming-guide/index.md)  
 [Atributy](../../../../../docs/standard/attributes/index.md)  
 [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Vytváření vlastních atributů (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
