---
title: Deklarace a odepření přístupu k prostředkům
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: df35ea2f01f96b044763c696434e5ede39d6b4bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715748"
---
# <a name="claims-and-denying-access-to-resources"></a>Deklarace a odepření přístupu k prostředkům
Windows Communication Foundation (WCF) podporuje mechanismus ověřování na základě deklarací identity. A také povolení přístupu k prostředkům na základě přítomnosti deklarace identity, systémy často zamítnutí přístupu k prostředkům na základě přítomnosti deklarací identity. Tyto systémy by měl prozkoumat <xref:System.IdentityModel.Policy.AuthorizationContext> pro deklarace identity, jejichž výsledkem je před hledáním deklarací, jejichž výsledkem je povolený přístup odepřen přístup.  
  
 Například může systém odepřít přístup k prostředku každému, kdo má deklaraci identity s typem z `Age`, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a hodnotu prostředků `Under 21` pouze pokud tuto identitu také má deklaraci typu `Name`, napravo od <xref:System.IdentityModel.Claims.Rights.Identity%2A>, a hodnota prostředků `Mallory`. Jinými slovy, systém odepře přístup všem uživatelům, kteří se do 21 let a udělí přístup, pokud je název Mallory. Pro správnou implementaci to sémantické, je důležité k vyhledání `Age` první deklarace identity a zjistit, jestli je stáří do 21 let. Jinak, pokud je v části 21 Mallory, pak prostředek udělit přístup pouze na základě těchto `Name` deklarací identity.  
  
## <a name="see-also"></a>Viz také:
- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Deklarace identity a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
