---
title: Jak definovat konstanty v jazyce C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 15526655de8af6fed464376db1ac761468215210
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337658"
---
# <a name="how-to-define-constants-in-c"></a>Jak definovat konstanty v C\#
Konstanty jsou pole, jejichž hodnoty jsou nastaveny v době kompilace a nikdy je nelze změnit. Konstanty slouží k poskytnutí smysluplných názvů namísto číselných literál ("magická čísla") pro speciální hodnoty.  
  
> [!NOTE]
> V jazyce C# direktivu preprocesoru [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) nelze použít k definování konstant způsobem, který se obvykle používá v jazyce C a C++.  
  
 Chcete-li definovat konstantní`int`hodnoty `byte`integrálních typů ( , , a tak dále) použijte ve výčtu. Další informace naleznete [v tématu výčet](../../language-reference/builtin-types/enum.md).  
  
 Chcete-li definovat neintegrální konstanty, jeden přístup `Constants`je jejich seskupení v jedné statické třídy s názvem . To bude vyžadovat, aby všechny odkazy na konstanty byly označeny názvem třídy, jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Použití kvalifikátoru názvu třídy pomáhá zajistit, že vy a ostatní, kteří používají konstantu, pochopíte, že je konstantní a nelze ji změnit.  
  
## <a name="see-also"></a>Viz také

- [Třídy a struky](./index.md)
