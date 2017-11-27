---
title: "Postupy: Definování konstant v jazyce C#"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ff12d0b6882289da9ed924f1c7de00edc5dc1e2e
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
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
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
