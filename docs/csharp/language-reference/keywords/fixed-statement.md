---
title: fixed – příkaz (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a>fixed – příkaz (Referenční dokumentace jazyka C#)
`fixed` Příkaz zabrání přemístění mobilní proměnné uvolňování paměti. `fixed` Příkazu je povolená jenom v [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu. `Fixed`Můžete také použít k vytvoření [pevnou velikost vyrovnávací paměti](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 `fixed` Příkaz nastaví ukazatel spravované proměnné a "PIN" tuto proměnnou během provádění příkazu. Bez `fixed`, ukazatele na mobilní spravované proměnné by být moc použití, protože uvolňování paměti by mohly přemístit proměnné nepředvídatelné. Kompilátor jazyka C# pouze umožňuje přiřadit ukazatel spravované proměnné v `fixed` příkaz.  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 Ukazatel lze inicializovat pomocí pole, řetězec, vyrovnávací paměti pevné velikosti nebo adresy proměnné. Následující příklad ukazuje použití proměnných adresy, pole a řetězce. Další informace o pevné velikosti vyrovnávací paměti najdete v tématu [pevnou velikost vyrovnávací paměti](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 Více ukazatele, bude možné inicializovat, dokud nebudou všechny stejného typu.  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 K chybě při inicializaci ukazatele různých typů, jednoduše vnořit `fixed` příkazy, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 Po spuštění kódu v příkazu, jsou všechny definovaného proměnné Odepnout a předmět pro uvolňování paměti. Proto neukazují na tyto proměnné mimo `fixed` příkaz.  
  
> [!NOTE]
>  Ukazatele v pevné příkazy inicializovat nemůže být upraven.  
  
 V režimu unsafe mohou přidělit paměť v zásobníku, kde se nevztahuje uvolňování paměti a proto nemusí být připojena. Další informace najdete v tématu [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [nezabezpečený](../../../csharp/language-reference/keywords/unsafe.md)  
 [Vyrovnávací paměti pevné velikosti](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
