---
title: Členové – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: 09802431d0a5954b67687e9878f572541eeaac79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705506"
---
# <a name="members-c-programming-guide"></a>Členové (Průvodce programováním v C#)

Třídy a struktury mají členy, které zastupují jejich data a chování. Členové třídy zahrnují všechny členy deklarované ve třídě spolu se všemi členy (s výjimkou konstruktorů a finalizačních metod) deklarovaných ve všech třídách v hierarchii dědičnosti. Soukromé členy základních tříd jsou zděděné, ale nejsou přístupné z odvozených tříd.  
  
 Následující tabulka uvádí seznam typů členů, které mohou třídy nebo struktury obsahovat:  
  
|Člen|Popis|  
|------------|-----------------|  
|[Pole](./fields.md)|Pole jsou proměnné deklarované v oboru třídy. Pole může být vestavěným číselným typem nebo instancí jiné třídy. Třída kalendáře může mít například pole obsahující aktuální datum.|  
|[Konstanty](./constants.md)|Konstanty jsou pole, jejichž hodnota je nastavena v době kompilace a nelze je změnit.|  
|[Vlastnosti](./properties.md)|Vlastnosti jsou metody ve třídě, které jsou přístupné, jako kdyby byly poli v dané třídě. Vlastnost může poskytovat ochranu pro pole třídy před změnou bez vědomí objektu.|  
|[Metody](./methods.md)|Metody definují akce, které mohou třídy provádět. Metody mohou přijímat parametry, které poskytují vstupní data, a mohou prostřednictvím parametrů vracet data. Metody mohou také vrátit hodnotu přímo, bez použití parametru.|  
|[Akce](../events/index.md)|Události poskytují upozorňování na různé události, jako například kliknutí na tlačítko nebo úspěšné dokončení metody, jiným objektům. Události jsou definovány a spouštěny pomocí delegátů.|  
|[Operátory](../../language-reference/operators/index.md)|Přetížené operátory jsou považovány za členy typu. Při přetížení operátor, definujete jako veřejné statické metody v typu. Další informace naleznete v tématu [Operator přetížení](../../language-reference/operators/operator-overloading.md).|  
|[Indexery](../indexers/index.md)|Indexery povolují objektu indexování způsobem podobným polím.|  
|[Konstruktory](./constructors.md)|Konstruktory jsou metody, které jsou volány při prvním vytvoření objektu. Často se používají k inicializaci dat objektu.|  
|[Finalizační metody](./destructors.md)|Finalizační metody se používají velmi zřídka v c#. Jsou to metody, které jsou volány spouštěcím modulem modulu runtime, když má být objekt odstraněn z paměti. Používají se obvykle k zajištění, aby veškeré prostředky, které musí být uvolněny, byly zpracovány správným způsobem.|  
|[Vnořené typy](./nested-types.md)|Vnořené typy jsou typy deklarované v rámci jiného typu. Vnořené typy se často používají k popisu objektů, které jsou používány pouze typy, jež je obsahují.|  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy](./classes.md)
