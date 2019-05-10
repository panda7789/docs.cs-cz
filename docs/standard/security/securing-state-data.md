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
ms.openlocfilehash: 85a12fb52efe32083d21b9aad50f2d9c1d6f0785
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602507"
---
# <a name="securing-state-data"></a>Zabezpečení stavových dat
Aplikace, které zpracovávají citlivé údaje nebo provádět jakýkoli druh rozhodnutí o zabezpečení je třeba ponechat data v rámci své vlastní ovládací prvek a nelze povolit další kódu potenciálně škodlivý přistupovat k datům. Nejlepší způsob, jak chránit data v paměti je deklarovat jako privátní nebo interní (s rozsahem omezené na stejné sestavení) proměnné. Však i tato data jsou v souladu s přístupu, které byste měli vědět:  
  
- Pomocí reflexe mechanismů, vysoce důvěryhodným kódem, který může odkazovat na objekt získat a nastavit privátní členy.  
  
- Pomocí serializace, vysoce důvěryhodným kódem můžete efektivně získat a nastavit privátní členy, pokud má přístup k odpovídající data ve formuláři serializovaného objektu.  
  
- V průběhu ladění, můžete tato data přečíst.  
  
 Ujistěte se, že žádná z vlastní metody nebo vlastnosti neúmyslně zpřístupňuje tyto hodnoty.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
