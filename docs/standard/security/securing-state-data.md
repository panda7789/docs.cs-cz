---
title: Zabezpečení stavových dat
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe941fff7091fb579e41a3c417dbb2129bcf3e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580780"
---
# <a name="securing-state-data"></a>Zabezpečení stavových dat
Aplikace, které zpracovávají důvěrná data nebo se přesvědčte, jakýkoli druh rozhodnutí týkající se zabezpečení je třeba ponechat data v rámci své vlastní ovládací prvek a nelze povolit další potenciálně škodlivého kódu, chcete-li získat přístup k datům. Nejlepší způsob, jak chránit data v paměti je deklarovat data jako soukromý nebo interní (s rozsahem omezené na stejném sestavení) proměnné. Ale i tato data jsou přístupná, byste měli vědět:  
  
-   Pomocí reflexe mechanismy, vysoce důvěryhodný kód, který může odkazovat objektu získat a nastavte soukromé členy.  
  
-   Pomocí serializace, vysoce důvěryhodný kód můžete efektivně získat a nastavit soukromé členy, pokud má přístup k odpovídající data ve formuláři serializovaného objektu.  
  
-   V části ladění, můžete tato data přečíst.  
  
 Zajistěte, aby že žádné metody nebo vlastnosti neúmyslně zpřístupňuje tyto hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
