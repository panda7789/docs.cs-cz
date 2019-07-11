---
title: Struktury – C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 063d7e3b68fbe6c01ff0df4ae935fec5af6f6891
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743846"
---
# <a name="structs-c-programming-guide"></a>Struktury (Průvodce programováním v C#)

Struktury jsou definované pomocí [struktura](../../language-reference/keywords/struct.md) – klíčové slovo, například:  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Struktury sdílet většina podle stejné syntaxe jako třídy. Název struktury musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md). Struktury jsou omezeny více než třídy následujícími způsoby:  
  
- V deklaraci struktury pole nelze inicializovat, jestliže nejsou deklarovány jako const nebo statické.  
- Struktury nelze deklarovat konstruktor bez parametrů (konstruktor bez parametrů) nebo finalizační metodu.  
- Struktury se zkopírují na přiřazení. Když je struktura přiřazena nové proměnné, se data kopírují a jakékoli změny nová kopie nezmění data pro původní kopírování. To je důležité pamatovat při práci s kolekcemi hodnoty typy, jako `Dictionary<string, myStruct>`.  
- Struktury jsou typy hodnot, na rozdíl od tříd, které jsou odkazové typy.  
- Na rozdíl od tříd, struktur dá vytvořit instance bez použití `new` operátor.  
- Struktury můžete deklarovat konstruktory, které mají parametry.
- Struktura nemůže dědit z jiné třídy nebo struktury a nemůže být základní třídy. Všechny struktury dědí přímo z <xref:System.ValueType>, který dědí z <xref:System.Object>.  
- Struktury můžou implementovat rozhraní.
- Struktura nemůže být `null`, a proměnnou struktury nelze přiřadit `null` Pokud je proměnná deklarována jako typ s možnou hodnotou Null.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](index.md)
- [Třídy](classes.md)
- [Typy s povolenou hodnotou Null](../nullable-types/index.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [Použití struktur](using-structs.md)
- [Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na metodu třídu](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
