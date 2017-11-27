---
title: "dynamic (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e3bf51ab62e195f7a5d1f0641f62380977c731ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dynamic-c-reference"></a>dynamic (Referenční dokumentace jazyka C#)
`dynamic` Typ umožňuje operace, ve kterých se vyskytuje obejít kontrolu typu v čase kompilace. Tyto operace jsou místo toho vyřešeny za běhu. `dynamic` Typ zjednodušuje přístup k rozhraní API modelu COM, jako je například rozhraní API Office automatizace a také pro dynamické rozhraní API, jako je například IronPython knihovny a k HTML Document Object Model (DOM).  
  
 Typ `dynamic` chová jako typ `object` ve většině případů. Ale operace, které obsahují výrazy typu `dynamic` se nevyřeší nebo typ zaškrtnutí kompilátorem. Doba běhu kompilátoru balíčky, které společně informace o operaci a tyto informace se později používá k vyhodnocení operaci. Jako součást procesu, proměnné typu `dynamic` kompilovány do proměnné typu `object`. Proto zadejte `dynamic` existuje pouze při kompilaci, není v době běhu.  
  
 V následujícím příkladu se liší od proměnné typu `dynamic` proměnné typu `object`. Ověření typu pro každou proměnnou v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v `WriteLine` příkazy. IntelliSense zobrazí **dynamické** pro `dyn` a **objekt** pro `obj`.  
  
 [!code-csharp[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 `WriteLine` Příkazy zobrazuje typy spuštění `dyn` a `obj`. V tomto bodě mají stejného typu, celé číslo. Vytváří následující výstup:  
  
 `System.Int32`  
  
 `System.Int32`  
  
 Rozdíl mezi `dyn` a `obj` při kompilaci, přidejte následující dva řádky mezi deklarací a `WriteLine` příkazy v předchozím příkladu.  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 Chyba kompilátoru hlášené pro pokus o přidání celé číslo a objekt ve výrazu `obj + 3`. Ale žádná chybová zpráva pro `dyn + 3`. Výraz, který obsahuje `dyn` kontrolována v době kompilace, protože typ `dyn` je `dynamic`.  
  
## <a name="context"></a>Kontext  
 `dynamic` – Klíčové slovo může vyskytovat přímo, nebo jako součást sady typu vytvořený v následujících situacích:  
  
-   V deklaracích jako typ vlastnost, pole, indexer, parametr vrátí hodnotu, místní proměnné, nebo zadejte omezení. Následující třídy definice používá `dynamic` v několika různých deklarace.  
  
     [!code-csharp[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   Při převodu explicitního typu jako cílový typ převodu z.  
  
     [!code-csharp[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   V libovolném kontextu, kde se typy sloužit jako hodnoty, například na pravé straně `is` operátor nebo `as` operátor, nebo jako argument `typeof` jako součást sestavené typu. Například `dynamic` lze použít v těchto výrazů.  
  
     [!code-csharp[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `dynamic` v několika deklarace. `Main` Metoda se také liší od kontroly s povolenou kontrolou běhového typu typu kompilaci.  
  
 [!code-csharp[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 Další informace a příklady naleznete v tématu [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [objekt](../../../csharp/language-reference/keywords/object.md)  
 [je](../../../csharp/language-reference/keywords/is.md)  
 [jako](../../../csharp/language-reference/keywords/as.md)  
 [typeof](../../../csharp/language-reference/keywords/typeof.md)  
 [Postupy: bezpečné přetypování pomocí jako a je operátory](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)  
 [Návod: Vytváření a používání dynamických objektů](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
