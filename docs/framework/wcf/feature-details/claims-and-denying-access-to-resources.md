---
title: Deklarace a odepření přístupu k prostředkům
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 4f48c59090579f4b451f615bb792a4dcb73f6df5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079510"
---
# <a name="claims-and-denying-access-to-resources"></a>Deklarace a odepření přístupu k prostředkům
Windows Communication Foundation (WCF) podporuje mechanismus ověřování na základě deklarací identity. A také povolení přístupu k prostředkům na základě přítomnosti deklarace identity, systémy často zamítnutí přístupu k prostředkům na základě přítomnosti deklarací identity. Tyto systémy by měl prozkoumat <xref:System.IdentityModel.Policy.AuthorizationContext> pro deklarace identity, jejichž výsledkem je před hledáním deklarací, jejichž výsledkem je povolený přístup odepřen přístup.  
  
 Například může systém odepřít přístup k prostředku každému, kdo má deklaraci identity s typem z `Age`, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a hodnotu prostředků `Under 21` pouze pokud tuto identitu také má deklaraci typu `Name`, napravo od <xref:System.IdentityModel.Claims.Rights.Identity%2A>, a hodnota prostředků `Mallory`. Jinými slovy, systém odepře přístup všem uživatelům, kteří se do 21 let a udělí přístup, pokud je název Mallory. Pro správnou implementaci to sémantické, je důležité k vyhledání `Age` první deklarace identity a zjistit, jestli je stáří do 21 let. Jinak, pokud je v části 21 Mallory, pak prostředek udělit přístup pouze na základě těchto `Name` deklarací identity.  
  
## <a name="see-also"></a>Viz také:

- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Deklarace identity a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
