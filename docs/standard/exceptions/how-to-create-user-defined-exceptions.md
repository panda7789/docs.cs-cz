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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708872"
---
# <a name="how-to-create-user-defined-exceptions"></a>Vytvoření uživatelsky definovaných výjimek

Rozhraní .NET poskytuje hierarchii tříd výjimek, které jsou nakonec odvozeny od <xref:System.Exception>základní třídy. Nicméně pokud žádná z předdefinovaných výjimek nevyhovuje vašim potřebám, můžete vytvořit vlastní třídy výjimek odvozením z třídy <xref:System.Exception>.

Při vytváření vlastních výjimek, ukončete název třídy uživatelsky definované výjimky slovem "Exception" a implementujte tři společné konstruktory, jak je znázorněno v následujícím příkladu. Příklad definuje novou třídu výjimky s názvem `EmployeeListNotFoundException`. Třída je odvozena z <xref:System.Exception> a obsahuje tři konstruktory.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> V situacích, kdy používáte vzdálenou komunikaci, je nutné zajistit, aby metadata pro všechny výjimky definované uživatelem byly k dispozici na serveru (volaném) a klientovi (objekt proxy nebo volající). Další informace najdete v tématu [osvědčené postupy pro výjimky](best-practices-for-exceptions.md).

## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
