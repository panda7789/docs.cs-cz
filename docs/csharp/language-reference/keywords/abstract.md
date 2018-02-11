---
title: "abstract (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9c6dbb03a05ff1c86752983d130691ce23e341d7
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="abstract-c-reference"></a>abstract (Referenční dokumentace jazyka C#)
`abstract` Modifikátor znamená, že je věcí upravována má implementace chybí nebo jsou neúplné. Abstraktní modifikátor lze použít s tříd, metod, vlastností, indexery a události. Použití `abstract` modifikátor v deklaraci třídy k označení, že třída je určen pouze k být základní třídy jiné třídy. Členy označené jako abstraktní, nebo součástí abstraktní třídu, musí být implementované třídy, které jsou odvozeny od abstraktní třídy.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída `Square` musí poskytovat implementace `Area` protože je odvozen z `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 Abstraktní třídy mají následující funkce:  
  
-   Nelze vytvořit instanci abstraktní třídy.  
  
-   Abstraktní třídy může obsahovat abstraktní metody a přístupové objekty.  
  
-   Není možné změnit abstraktní třídy [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) modifikátor protože dvě modifers mají opačné významy. `sealed` Modifikátor brání třídy dědí a `abstract` modifikátor vyžaduje zděděná třída.  
  
-   Neabstraktní třídy odvozené od abstraktní třídy musí obsahovat Skutečná implementace všechny zděděné abstraktní metody a přístupové objekty.  
  
 Použití `abstract` modifikátor v deklaraci metody nebo vlastnosti k označení metody nebo vlastnosti neobsahuje implementace.  
  
 Abstraktní metody mají následující funkce:  
  
-   Abstraktní metodu je implicitně virtuální metoda.  
  
-   Abstraktní metodu deklarace jsou povolena pouze v abstraktní třídy.  
  
-   Vzhledem k tomu, že deklarace abstraktní metody poskytuje žádný skutečný implementaci, není žádná metoda textu; deklarace metody jednoduše končí středníkem a neexistují žádné složené závorky ({}), následující podpis. Příklad:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Poskytuje implementaci metodu [přepsat](../../../csharp/language-reference/keywords/override.md), který je členem jinou než abstraktní třídou.  
  
-   Jedná se o chybu používat [statické](../../../csharp/language-reference/keywords/static.md) nebo [virtuální](../../../csharp/language-reference/keywords/virtual.md) modifikátory v deklarace abstraktní metody.  
  
 Abstraktní vlastnosti chovat jako abstraktní metody, s výjimkou rozdíly v syntaxi deklarace a volání.  
  
-   Jedná se o chybu používat `abstract` modifikátor na pomocí statické vlastnosti.  
  
-   Abstraktní zděděnou vlastnost je možné přepsat v odvozené třídě včetně deklarace vlastnosti, která používá [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor.  
  
 Další informace o abstraktní třídy najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Abstraktní třída musí poskytovat implementace pro všechny členy rozhraní.  
  
 Abstraktní třída, která implementuje rozhraní může mapování metod rozhraní na abstraktní metody. Příklad:  
  
 [!code-csharp[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída `DerivedClass` je odvozený z abstraktní třídy `BaseClass`. Abstraktní třída obsahuje metody abstraktní `AbstractMethod`a dvě abstraktní vlastnosti `X` a `Y`.  
  
 [!code-csharp[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 V předchozím příkladu, pokud se pokusíte vytvořit instanci abstraktní třídy za použití příkazu takto:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Zobrazí se chyba s oznámením, že kompilátor nelze vytvořit instanci abstraktní třídy 'Baseclass –'.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
