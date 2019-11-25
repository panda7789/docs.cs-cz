---
title: Struktury – C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 35b39da0b15c41b7b2c7a6567bea5dca3fb430e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970322"
---
# <a name="structs-c-programming-guide"></a>Struktury (Průvodce programováním v C#)

Struktury jsou definované pomocí klíčového slova [struct](../../language-reference/keywords/struct.md) , například:  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Struktury sdílejí většinu stejné syntaxe jako třídy. Název struktury musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md). Struktury jsou více omezené než třídy následujícími způsoby:  
  
- V rámci deklarace struktury nelze pole inicializovat, pokud nejsou deklarována jako const nebo static.  
- Struktura nemůže deklarovat konstruktor bez parametrů (konstruktor bez parametrů) nebo finalizační metodu.  
- Struktury se zkopírují při přiřazení. Když je struktura přiřazena nové proměnné, zkopírují se všechna data a jakákoli změna nové kopie nemění data původní kopie. To je důležité pamatovat při práci s kolekcemi typů hodnot, jako je `Dictionary<string, myStruct>`.  
- Struktury jsou typy hodnot, na rozdíl od tříd, které jsou odkazové typy.  
- Na rozdíl od tříd lze vytvořit instanci struktur bez použití operátoru `new`.  
- Struktury mohou deklarovat konstruktory, které mají parametry.
- Struktura nemůže dědit z jiné struktury nebo třídy a nemůže být základem třídy. Všechny struktury dědí přímo z <xref:System.ValueType>, které dědí z <xref:System.Object>.  
- Struktura může implementovat rozhraní.
- Strukturu nelze `null`a proměnnou struktury nelze přiřadit `null`, pokud je proměnná deklarována jako typ hodnoty s možnou hodnotou null.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](index.md)
- [Třídy](classes.md)
- [Typy hodnot s možnou hodnotou null](../../language-reference/builtin-types/nullable-value-types.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [Použití struktur](using-structs.md)
- [Jak zjistit rozdíl mezi předáním struktury a předáním odkazu na třídu metodě](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
