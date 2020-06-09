---
title: Deklarace a odepření přístupu k prostředkům
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: e5ecb71b7e0596b1732207b50e1b6087528bba3f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587037"
---
# <a name="claims-and-denying-access-to-resources"></a>Deklarace a odepření přístupu k prostředkům
Windows Communication Foundation (WCF) podporuje mechanismus ověřování založený na deklaracích. I přístup k prostředkům na základě přítomnosti deklarací identity systémy často odmítají přístup k prostředkům na základě přítomnosti deklarací identity. Tyto systémy by měly <xref:System.IdentityModel.Policy.AuthorizationContext> u deklarací identity, které mají za následek odepření přístupu, prozkoumávat před vyhledáním deklarací identity, jejichž výsledkem je povolený přístup.  
  
 Systém může například odepřít přístup k prostředku všem, kdo má deklaraci identity s typem `Age` , napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> a hodnotou prostředku `Under 21` pouze v případě, že tato identita má také deklaraci identity typu `Name` , napravo od <xref:System.IdentityModel.Claims.Rights.Identity%2A> a s hodnotou prostředku `Mallory` . Jinak systém zamítne přístup všem, kteří jsou mladší 21 let, a udělí přístup, pokud je název Mallory. Aby bylo možné tuto sémantickou implementaci správně implementovat, je důležité `Age` nejdřív vyhledat deklaraci identity a zjistit, jestli je stáří mladší 21 let. V opačném případě, pokud má Mallory pod 21, může být prostředku udělen přístup výhradně na základě `Name` deklarace identity.  
  
## <a name="see-also"></a>Viz také

- [Správa deklarací a autorizace s modelem identity](managing-claims-and-authorization-with-the-identity-model.md)
- [Deklarace a tokeny](claims-and-tokens.md)
