---
title: abstraktní - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 325be8851b63a252c381d943943937332ec91e6b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638038"
---
# <a name="abstract-c-reference"></a>abstract (Referenční dokumentace jazyka C#)
`abstract` Modifikátor znamená, že věc, kterou právě upravuje má chybějící či neúplné implementace. Modifikátor abstract jde použít s třídy, metody, vlastnosti, indexery a události. Použití `abstract` modifikátor v deklaraci třídy k označení, že třída je určen pouze k být základní třídou jiné třídy. Členy označené jako abstraktní, nebo součástí abstraktní třídu, musí být implementované třídami, které jsou odvozeny od abstraktní třídy.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída `Square` musí zajišťovat implementaci rozhraní `Area` protože se odvozuje od `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Abstraktní třídy mají následující funkce:  
  
-   Nelze vytvořit instanci abstraktní třídy.  
  
-   Abstraktní třída může obsahovat abstraktní metody a přístupové objekty.  
  
-   Není možné změnit abstraktní třídy [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) modifikátor vzhledem k tomu, že mají dva modifers opačné význam. `sealed` Modifikátor zabraňuje třídy děděny a `abstract` vyžaduje Modifikátor třídy odvozeny.  
  
-   Neabstraktní třídy odvozené od abstraktní třídy musí obsahovat Skutečná implementace všechny zděděné abstraktní metody a přístupové objekty.  
  
 Použití `abstract` modifikátor v deklaraci metody nebo vlastnosti k označení, že metoda nebo vlastnost neobsahuje implementaci.  
  
 Abstraktní metody nemají následující funkce:  
  
-   Abstraktní metoda je implicitně virtuální metody.  
  
-   Deklarace abstraktní metody jsou povolené jenom v abstraktní třídy.  
  
-   Protože deklarací abstraktní metody poskytuje skutečné implementaci, neexistuje žádné tělo metody; deklarace metody jednoduše končí středníkem a neexistují žádné složených závorek ({}) po podpisu. Příklad:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Poskytuje implementaci metody [přepsat](../../../csharp/language-reference/keywords/override.md), který je členem skupiny jinou než abstraktní třídou.  
  
-   Jedná se o chybu používat [statické](../../../csharp/language-reference/keywords/static.md) nebo [virtuální](../../../csharp/language-reference/keywords/virtual.md) modifikátorů v deklarací abstraktní metody.  
  
 Abstraktní vlastnosti se chovají stejně jako abstraktní metody, s výjimkou rozdílů v syntaxi deklarace a volání.  
  
-   Jedná se o chybu používat `abstract` modifikátor statickou vlastnost.  
  
-   Zděděný abstraktní vlastnost možné přepsat v odvozené třídě včetně, která používá deklarace vlastnosti [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor.  
  
 Další informace o abstraktních tříd naleznete v tématu [abstraktní a zapečetěné třídy a členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Abstraktní třídy musí poskytnout implementaci pro všechny členy rozhraní.  
  
 Abstraktní třídu, která implementuje rozhraní namapovat metody rozhraní na abstraktní metody. Příklad:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída `DerivedClass` je odvozen z abstraktní třídy `BaseClass`. Abstraktní třída obsahuje abstraktní metoda `AbstractMethod`a dvě abstraktních a vlastností, `X` a `Y`.  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 V předchozím příkladu, pokud se pokusíte vytvořit instanci abstraktní třídy za použití příkazu takto:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Zobrazí se chyba s oznámením, že kompilátor nelze vytvořit instanci abstraktní třídy "BaseClass".  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
- [virtual](../../../csharp/language-reference/keywords/virtual.md)
- [override](../../../csharp/language-reference/keywords/override.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
