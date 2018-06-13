---
title: 'Postupy: Definování konstant v jazyce C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 03912a71aba883ec9127d265e6f1a2b05e1e60fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313219"
---
# <a name="how-to-define-constants-in-c"></a>Postupy: Definování konstant v jazyce C#
Konstanty jsou pole, jejichž hodnoty jsou nastaveny na doba kompilace a nelze je změnit. Pomocí konstanty pro zajištění speciální hodnoty smysluplné názvy místo číselné literály ("čísla magic").  
  
> [!NOTE]
>  V jazyce C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) direktivy preprocesoru nelze použít k definování konstant ve způsobu, jakým se obvykle používá v C a C++.  
  
 K definování konstantní hodnoty celočíselných typů (`int`, `byte`a tak dále) použít výčtového typu. Další informace najdete v tématu [výčtu](../../../csharp/language-reference/keywords/enum.md).  
  
 K definování konstant celé číslo, jeden z přístupů je seskupovat je do jedné statické třídy s názvem `Constants`. To bude vyžadovat, aby všechny odkazy na konstanty být uvedena názvu třídy, jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 Použití kvalifikátor název třídy pomáhá uživatelů použijte konstantu jasné, že je konstantní a nemůže být upraven.  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
