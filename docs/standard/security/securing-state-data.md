---
title: Zabezpečení stavových dat
description: Deklarujte data stavu jako soukromé nebo interní proměnné, které omezí přístup k nim. Tato data lze stále přistupovat prostřednictvím reflexe, serializace a ladění.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: f95bf409f7eef8c2636d3c180d2bbd95fbc689c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186828"
---
# <a name="securing-state-data"></a>Zabezpečení stavových dat
Aplikace, které zpracovávají citlivá data nebo dělají jakékoli rozhodnutí o zabezpečení, musí tato data uchovávat pod vlastní kontrolou a nemohou povolit přímý přístup k datům jinému potenciálně škodlivému kódu. Nejlepší způsob, jak chránit data v paměti je deklarovat data jako soukromé nebo interní (s rozsahem omezena na stejné sestavení) proměnné. Nicméně, i tyto údaje jsou předmětem přístupu, měli byste si být vědomi:  
  
- Pomocí reflexe mechanismy, vysoce důvěryhodný kód, který může odkazovat na objekt můžete získat a nastavit soukromé členy.  
  
- Pomocí serializace může vysoce důvěryhodný kód efektivně získat a nastavit soukromé členy, pokud má přístup k odpovídajícím datům v serializované podobě objektu.  
  
- Při ladění lze tato data číst.  
  
 Ujistěte se, že žádné z vlastních metod nebo vlastností neúmyslně nezveřejňuje tyto hodnoty.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
