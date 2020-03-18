---
title: abstraktní - C# Reference
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 96e8bbce2e67c316d5cd1cd78e3e2506dabead25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713855"
---
# <a name="abstract-c-reference"></a>abstract (Referenční dokumentace jazyka C#)
Modifikátor `abstract` označuje, že upravovaná věc má chybějící nebo neúplnou implementaci. Abstraktní modifikátor lze použít s třídami, metodami, vlastnostmi, indexery a událostmi. `abstract` Modifikátor v deklaraci třídy označuje, že třída je určena pouze jako základní třída jiných tříd, není vytvořena sama. Členy označené jako abstraktní musí být implementovány neabstraktní třídy, které jsou odvozeny z abstraktní třídy.
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Square` musí třída `GetArea` poskytnout implementaci, `Shape`protože je odvozena z :  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Abstraktní třídy mají následující funkce:  
  
- Abstraktní třídu nelze vytvořit instanci.  
  
- Abstraktní třída může obsahovat abstraktní metody a přistupující objekty.  
  
- Není možné upravit abstraktní třídu s [uzavřeným](./sealed.md) modifikátorem, protože dva modifikátory mají opačný význam. Modifikátor `sealed` zabraňuje zdědění třídy a `abstract` modifikátor vyžaduje, aby byla třída zděděna.  
  
- Neabstraktní třída odvozená z abstraktní třídy musí obsahovat skutečné implementace všech zděděných abstraktních metod a přistupujících objektů.  
  
 `abstract` Modifikátor v deklaraci metody nebo vlastnosti označte, že metoda nebo vlastnost neobsahuje implementaci.  
  
 Abstraktní metody mají následující funkce:  
  
- Abstraktní metoda je implicitně virtuální metoda.  
  
- Deklarace abstraktní metody jsou povoleny pouze v abstraktních třídách.  
  
- Vzhledem k tomu, že deklarace abstraktní metody neposkytuje žádnou skutečnou implementaci, neexistuje žádné tělo metody; Deklarace metody jednoduše končí středníkem a neexistují žádné složené závorky ({ }) za podpisem. Například:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Implementace je poskytována [přepsáním](./override.md)metody , která je členem neabstraktní třídy.  
  
- Je chyba použít [statické](./static.md) nebo [virtuální](./virtual.md) modifikátory v deklaraci abstraktní metody.  
  
 Abstraktní vlastnosti se chovají jako abstraktní metody, s výjimkou rozdílů v syntaxi deklarace a vyvolání.  
  
- Je chyba použít `abstract` modifikátor na statickou vlastnost.  
  
- Abstraktní zděděná vlastnost může být přepsána v odvozené třídě zahrnutím deklarace vlastnosti, která používá modifikátor [přepsání.](./override.md)  
  
 Další informace o abstraktních třídách naleznete v [tématu Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Abstraktní třída musí poskytovat implementaci pro všechny členy rozhraní.  
  
 Abstraktní třída, která implementuje rozhraní může mapovat metody rozhraní na abstraktní metody. Například:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Příklad  
 V tomto příkladu `DerivedClass` je třída odvozena `BaseClass`z abstraktní třídy . Abstraktní třída obsahuje abstraktní `AbstractMethod`metodu a dvě `X` `Y`abstraktní vlastnosti a .  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 V předchozím příkladu pokud se pokusíte vytvořit instanci abstraktní třídy pomocí příkazu, jako je tento:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Zobrazí se chyba, že kompilátor nemůže vytvořit instanci abstraktní třídy BaseClass.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Modifikátory](index.md)
- [virtual](./virtual.md)
- [override](./override.md)
- [C# Klíčová slova](./index.md)
