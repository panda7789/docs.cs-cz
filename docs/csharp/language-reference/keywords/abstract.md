---
description: abstract – reference jazyka C#
title: abstract – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 095c4dea838aff4f14833d78fb10a2f831cf5173
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127201"
---
# <a name="abstract-c-reference"></a>abstract (Referenční dokumentace jazyka C#)
`abstract`Modifikátor označuje, že upravená věc má chybějící nebo nekompletní implementaci. Modifikátor abstract lze použít se třídami, metodami, vlastnostmi, indexery a událostmi. Použijte `abstract` Modifikátor v deklaraci třídy k označení, že třída je určena pouze pro základní třídu jiných tříd, nikoli na vlastní instanci. Členy označené jako abstraktní musí být implementovány neabstraktními třídami odvozenými z abstraktní třídy.
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída `Square` musí poskytovat implementaci, `GetArea` protože je odvozena z `Shape` :  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Abstraktní třídy mají následující funkce:  
  
- Nelze vytvořit instanci abstraktní třídy.  
  
- Abstraktní třída může obsahovat abstraktní metody a přistupující objekty.  
  
- Není možné změnit abstraktní třídu s [zapečetěným](./sealed.md) modifikátorem, protože dva modifikátory mají opačné významy. `sealed`Modifikátor zabraňuje dědění třídy a `abstract` Modifikátor vyžaduje dědění třídy.  
  
- Neabstraktní třída odvozená z abstraktní třídy musí zahrnovat skutečné implementace všech zděděných abstraktních metod a přístupových objektů.  
  
 Použijte `abstract` Modifikátor v deklaraci metody nebo vlastnosti, abyste označili, že metoda nebo vlastnost neobsahuje implementaci.  
  
 Abstraktní metody mají následující funkce:  
  
- Abstraktní metoda je implicitně virtuální metodou.  
  
- Deklarace abstraktní metody jsou povolené jenom v abstraktních třídách.  
  
- Vzhledem k tomu, že deklarace abstraktní metody neposkytuje žádnou skutečnou implementaci, neexistuje tělo metody; deklarace metody jednoduše končí středníkem a za signaturou neexistují žádné složené závorky ({}). Příklad:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Implementace je poskytována [přepsáním](./override.md)metody, která je členem neabstraktní třídy.  
  
- Použití [statických](./static.md) nebo [virtuálních](./virtual.md) modifikátorů v deklaraci abstraktní metody je chyba.  
  
 Abstraktní vlastnosti se chovají jako abstraktní metody, s výjimkou rozdílů v deklaraci a syntaxi vyvolání.  
  
- Použití `abstract` modifikátoru na statické vlastnosti je chybné.  
  
- Abstraktní zděděná vlastnost může být přepsána v odvozené třídě zahrnutím deklarace vlastnosti, která používá modifikátor [přepsání](./override.md) .  
  
 Další informace o abstraktních třídách naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Abstraktní třída musí poskytovat implementaci pro všechny členy rozhraní.  
  
 Abstraktní třída, která implementuje rozhraní, může mapovat metody rozhraní na abstraktní metody. Příklad:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Příklad  
 V tomto příkladu `DerivedClass` je třída odvozena z abstraktní třídy `BaseClass` . Abstraktní třída obsahuje abstraktní metodu, `AbstractMethod` a dvě abstraktní vlastnosti `X` a `Y` .  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 Pokud se v předchozím příkladu pokusíte vytvořit instanci abstraktní třídy pomocí příkazu podobného tomuto:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Zobrazí se chyba oznamující, že kompilátor nemůže vytvořit instanci abstraktní třídy ' BaseClass '.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Modifikátory](index.md)
- [virtual](./virtual.md)
- [override](./override.md)
- [Klíčová slova jazyka C#](./index.md)
