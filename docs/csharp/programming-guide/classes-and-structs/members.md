---
title: Členové (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: 61818b153bb74c5c0da053f381fd1ed9132c066b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318221"
---
# <a name="members-c-programming-guide"></a>Členové (Průvodce programováním v C#)
Třídy a struktury mají členy, které zastupují jejich data a chování. Členy třídy a zahrnují všechny deklarované členy ve třídě, společně s všechny členy (s výjimkou konstruktory a finalizační metody) deklarované v všechny třídy v hierarchii dědičnosti. Soukromé členy základních tříd jsou zděděné, ale nejsou přístupné z odvozených tříd.  
  
 Následující tabulka uvádí seznam typů členů, které mohou třídy nebo struktury obsahovat:  
  
|Člen|Popis|  
|------------|-----------------|  
|[Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)|Pole jsou proměnné deklarované v oboru třídy. Pole může být vestavěným číselným typem nebo instancí jiné třídy. Třída kalendáře může mít například pole obsahující aktuální datum.|  
|[Konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md)|Konstanty jsou pole nebo vlastnosti, jejichž hodnota je nastavena v době kompilace a nelze ji změnit.|  
|[Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)|Vlastnosti jsou metody ve třídě, které jsou přístupné, jako kdyby byly poli v dané třídě. Vlastnost může poskytovat ochranu pro pole třídy před změnou bez vědomí objektu.|  
|[Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)|Metody definují akce, které mohou třídy provádět. Metody mohou přijímat parametry, které poskytují vstupní data, a mohou prostřednictvím parametrů vracet data. Metody mohou také vrátit hodnotu přímo, bez použití parametru.|  
|[Události](../../../csharp/programming-guide/events/index.md)|Události poskytují upozorňování na různé události, jako například kliknutí na tlačítko nebo úspěšné dokončení metody, jiným objektům. Události jsou definovány a spouštěny pomocí delegátů.|  
|[Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Přetížené operátory jsou považovány za členy třídy. Pokud přetížíte operátor, definujete ho jako veřejnou statickou metodu ve třídě. Předdefinované operátory (`+`, `*`, `<` atd.) nejsou považovány za členy. Další informace najdete v tématu [přetížitelné operátory](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).|  
|[Indexery](../../../csharp/programming-guide/indexers/index.md)|Indexery povolují objektu indexování způsobem podobným polím.|  
|[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Konstruktory jsou metody, které jsou volány při prvním vytvoření objektu. Často se používají k inicializaci dat objektu.|  
|[Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)|Finalizační metody v jazyce C# používají velmi zřídka. Jsou to metody, které jsou volány spouštěcím modulem modulu runtime, když má být objekt odstraněn z paměti. Používají se obvykle k zajištění, aby veškeré prostředky, které musí být uvolněny, byly zpracovány správným způsobem.|  
|[Vnořené typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|Vnořené typy jsou typy deklarované v rámci jiného typu. Vnořené typy se často používají k popisu objektů, které jsou používány pouze typy, jež je obsahují.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [Vnořené typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
 [Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
 [Přetížitelné operátory](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)
