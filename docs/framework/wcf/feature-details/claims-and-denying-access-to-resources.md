---
title: Deklarace a odepření přístupu k prostředkům
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: a53affe5e21b5ef532e7094eed032b44f5a5ea7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488608"
---
# <a name="claims-and-denying-access-to-resources"></a>Deklarace a odepření přístupu k prostředkům
Windows Communication Foundation (WCF) podporuje mechanismus ověřování založené na deklaracích identity. A také povolení přístup k prostředkům na základě přítomnosti deklarací identity, systémy často odepřít přístup k prostředkům na základě přítomnosti deklarací identity. Tyto systémy měli zkontrolovat <xref:System.IdentityModel.Policy.AuthorizationContext> pro deklarace identity, jejichž výsledkem je před hledáním deklarace identity, jejichž výsledkem je povolen přístup odepřen přístup.  
  
 Například může systém odepřít přístup k prostředku na každý, kdo má deklarace identity s typem z `Age`, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a hodnota prostředků `Under 21` pouze když tuto identitu má také deklarace identity typu `Name`, napravo od <xref:System.IdentityModel.Claims.Rights.Identity%2A>, a hodnota prostředků `Mallory`. Jinými slovy, systém odepře přístup všem uživatelům, kteří je do 21 let a udělí přístup, pokud je název Mallory. Toto správně implementovat sémantického, je důležité Hledat `Age` nejprve deklarace identity a určit, zda je stáří do 21 let. Jinak, pokud Mallory je v části 21, pak prostředku může mít udělen přístup výhradně na základě těchto `Name` deklarací identity.  
  
## <a name="see-also"></a>Viz také  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Deklarace identity a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
