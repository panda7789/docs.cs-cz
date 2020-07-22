---
title: Jak definovat konstanty v jazyce C#
description: Naučte se definovat konstanty v jazyce C#, což jsou pole, jejichž hodnoty jsou nastaveny v době kompilace. Použijte konstanty k poskytnutí smysluplných názvů pro speciální hodnoty.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: afa2799cf76f976e332f91b631dc90e2799a0aa0
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864641"
---
# <a name="how-to-define-constants-in-c"></a>Definování konstant v jazyce C\#
Konstanty jsou pole, jejichž hodnoty jsou nastaveny v době kompilace a nelze je nikdy změnit. Použijte konstanty k poskytnutí smysluplných názvů namísto číselných literálů ("Magic Numbers") pro speciální hodnoty.  
  
> [!NOTE]
> V jazyce C# nelze pomocí direktivy preprocesoru [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) definovat konstanty způsobem, který je obvykle používán v jazyce C a C++.  
  
 Pro definování konstantních hodnot integrálních typů ( `int` , a `byte` tak dále) použijte Výčtový typ. Další informace naleznete v tématu [Enum](../../language-reference/builtin-types/enum.md).  
  
 Chcete-li definovat Neceločíselné konstanty, jedním z přístupů je seskupit do jedné statické třídy s názvem `Constants` . To bude vyžadovat, aby všechny odkazy na konstanty byly uvozeny názvem třídy, jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Použití kvalifikátoru názvu třídy pomáhá zajistit, aby vy a ostatní uživatelé používali konstantu, což znamená, že je konstantní a nelze ji upravit.  
  
## <a name="see-also"></a>Viz také

- [Třídy a struktury](./index.md)
