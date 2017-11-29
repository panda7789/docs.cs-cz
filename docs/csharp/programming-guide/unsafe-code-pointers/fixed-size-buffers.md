---
title: "Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)
V jazyce C#, můžete použít [pevné](../../../csharp/language-reference/keywords/fixed-statement.md) příkaz k vytvoření vyrovnávací paměti s pevnou velikost pole ve struktuře data. To je užitečné, když pracujete s existující kód, jako je například kód napsaný v jiných jazycích, existující knihovny DLL nebo COM projekty. Pole pevné může trvat všechny atributy nebo modifikátory, které jsou povoleny pro regulární struktura členy. Pouze omezení je, že musí být typ pole `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, nebo `double`.  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a>Poznámky  
 Deklarace struktury pevné velikosti styl C++ byla obtížná v dřívějších verzích programu C#, protože struktury jazyka C# obsahující pole neobsahuje prvků pole. Místo toho struct obsahuje odkaz na elementy.  
  
 Přidání možnosti pro vložení pole s pevnou velikostí v 2.0 C# [struktura](../../../csharp/language-reference/keywords/struct.md) při použití v [unsafe](../../../csharp/language-reference/keywords/unsafe.md) blok kódu.  
  
 Například před C# 2.0, následující `struct` by velikosti 8 bajtů. `pathName` Pole je odkaz na pole přidělené haldy:  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 Od verze 2.0 C# `struct` může obsahovat vložené pole. V následujícím příkladu `fixedBuffer` pole má pevnou velikost. Chcete-li získat přístup k elementy pole, použijte `fixed` příkaz k vytvoření ukazatel na první prvek. `fixed` Příkaz PIN kódy instanci `fixedBuffer` do určitého umístění v paměti.  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 Velikost 128 elementu `char` pole je 256 bajtů. Pevná velikost [char](../../../csharp/language-reference/keywords/char.md) vyrovnávací paměti vždy provést dva bajty na znak, bez ohledu na to, kódování. To platí i když vyrovnávací paměti char přeuspořádány metody rozhraní API nebo struktury s `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi`. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.  
  
 Další běžné pole pevné velikosti je [bool](../../../csharp/language-reference/keywords/bool.md) pole. Prvky v `bool` pole jsou vždy jeden bajt velikost. `bool`pole nejsou vhodné pro vytváření bitová pole nebo vyrovnávací paměti.  
  
> [!NOTE]
>  S výjimkou paměti vytvořené pomocí [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), kompilátor jazyka C# a modul CLR (CLR) neprovádějte žádné kontroly přetečení vyrovnávací paměti zabezpečení. Stejně jako u všech nezabezpečený kód, buďte opatrní.  
  
 Nezabezpečené vyrovnávací paměti se liší od regulární pole následujícími způsoby:  
  
-   Nezabezpečené vyrovnávací paměti můžete použít pouze v kontextu unsafe.  
  
-   Nezabezpečené vyrovnávací paměti jsou vždy vektory nebo jednorozměrná pole.  
  
-   Deklarace pole by měla obsahovat počet, jako například `char id[8]`. Nemůžete použít `char id[]` místo.  
  
-   Nezabezpečené vyrovnávací paměti lze pouze pole instance struktury v kontextu unsafe.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Vzájemná funkční spolupráce](../../../csharp/programming-guide/interop/index.md)
