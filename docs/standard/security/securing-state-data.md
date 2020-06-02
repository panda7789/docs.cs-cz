---
title: Zabezpečení stavových dat
description: Deklaruje stavová data jako privátní nebo interní proměnné pro omezení přístupu k ní. Tato data jsou stále k dispozici prostřednictvím reflexe, serializace a ladění.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: b7fcb520fe6fa28cc098c4e1cbb56ce7da759c11
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291042"
---
# <a name="securing-state-data"></a>Zabezpečení stavových dat
Aplikace, které zpracovávají citlivá data nebo mohou učinit jakékoli rozhodnutí o zabezpečení, musí uchovávat tato data pod svým vlastním ovládacím prvkem a nemohou jiným potenciálně škodlivému kódu přistupovat přímo k datům. Nejlepším způsobem, jak chránit data v paměti, je deklarovat data jako privátní nebo interní (s oborem omezeným na stejné sestavení). I tato data však podléhají přístupu, na které byste měli vědět:  
  
- Pomocí mechanismů reflexe, vysoce důvěryhodného kódu, který může odkazovat na váš objekt, mohou získat a nastavit soukromé členy.  
  
- Pomocí serializace může vysoce důvěryhodný kód efektivně získat a nastavit soukromé členy, pokud mají přístup k odpovídajícím datům v serializované podobě objektu.  
  
- V části ladění lze tato data číst.  
  
 Ujistěte se, že žádná z vašich vlastních metod ani vlastností tyto hodnoty neúmyslně zveřejňuje.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](secure-coding-guidelines.md)
