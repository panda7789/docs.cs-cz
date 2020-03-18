---
title: 'Postupy: Vytváření uživatelsky definovaných výjimek'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: 6de00490a17fff005dd50a7acc5247089c073f68
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708872"
---
# <a name="how-to-create-user-defined-exceptions"></a>Jak vytvořit uživatelem definované výjimky

Rozhraní .NET poskytuje hierarchii tříd výjimek, <xref:System.Exception>které jsou nakonec odvozeny ze základní třídy . Pokud však žádná z předdefinovaných výjimek nevyhovuje vašim potřebám, můžete vytvořit <xref:System.Exception> vlastní třídy výjimek odvozením z třídy.

Při vytváření vlastní výjimky, konec název třídy uživatelem definované výjimky se slovem "Výjimka" a implementovat tři společné konstruktory, jak je znázorněno v následujícím příkladu. Příklad definuje novou třídu `EmployeeListNotFoundException`výjimek s názvem . Třída je odvozena <xref:System.Exception> od a zahrnuje tři konstruktory.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> V situacích, kdy používáte vzdálené volání, je nutné zajistit, aby metadata pro všechny uživatelem definované výjimky byla k dispozici na serveru (volaný) a klientovi (objekt proxy nebo volající). Další informace naleznete v [tématu Doporučené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
