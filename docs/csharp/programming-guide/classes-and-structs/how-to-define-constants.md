---
title: 'Postupy: Definování konstant v jazyce C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 09d19f708570b55509a3ec2a41e439cb9c9de973
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540229"
---
# <a name="how-to-define-constants-in-c"></a>Postupy: Definování konstant v jazyce C#
Konstanty jsou pole, jejichž hodnoty se nastavují v době kompilace a nikdy se dá změnit. Použijte k poskytnutí smysluplné názvy namísto číselných literálů ("čísla magic") pro zvláštní hodnoty konstant.  
  
> [!NOTE]
>  V jazyce C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) direktivy preprocesoru nelze použít pro definování konstant ve způsobu, jakým se obvykle používá v jazyce C a C++.  
  
 Pro definování hodnot konstanty celočíselných typů (`int`, `byte`, a tak dále) použijte výčtového typu. Další informace najdete v tématu [výčtu](../../../csharp/language-reference/keywords/enum.md).  
  
 Definovat konstanty neintegrálních, jedním z přístupů je seskupovat je do jedné statickou třídu s názvem `Constants`. To vyžaduje, aby všechny odkazy na konstanty být uvozena řetězcem názvu třídy, jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 Použití kvalifikátoru název třídy pomáhá, ujistěte se, že můžete vy a ostatní, kteří používají konstanta pochopit, že je konstantní a nelze ji změnit.  
  
## <a name="see-also"></a>Viz také

- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
