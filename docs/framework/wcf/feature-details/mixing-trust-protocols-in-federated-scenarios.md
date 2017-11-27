---
title: "Smíšené používání protokolů Trust ve federovaných scénářích"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 007dec81766423ea2826e98ae0b6b399a1508f11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Smíšené používání protokolů Trust ve federovaných scénářích
Mohou existovat scénáře ve kterých federované klienti komunikují se službou a tokenu služby zabezpečení (STS), které nemají stejnou verzi vztah důvěryhodnosti. Služby mohou obsahovat WSDL `RequestSecurityTokenTemplate` assertion WS-Trust elementy, které jsou různé verze než Služba tokenů zabezpečení. V takových případech [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] převede WS-Trust elementy přijaté z klienta `RequestSecurityTokenTemplate` tak, aby odpovídaly Služba tokenů zabezpečení důvěřovat verze. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obslužné rutiny neshoda verze důvěryhodnosti pouze pro standardní vazby. Všechny standardní algoritmus parametry, které jsou rozpoznáno [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou součástí standardní vazby. Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chování s různými důvěřovat nastavení mezi služba a služba tokenů zabezpečení.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP únor 2005 a služby tokenů zabezpečení únor 2005  
 WSDL pro předávající strany (RP) obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Konfigurační soubor klienta obsahuje seznam parametrů.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nelze rozlišit mezi klientem a službou parametry; Přidá všechny parametry a odešle je v `RequestSecurityTokenTemplate` (RVNÍ).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>Vztah důvěryhodnosti RP 1.3 a vztah důvěryhodnosti služby tokenů zabezpečení 1.3  
 WSDL pro RP obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Konfigurační soubor klienta obsahuje `secondaryParameters` element, který zabalí parametry určeného RP.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Odebere `EncryptionAlgorithm`, `CanonicalizationAlgorithm` a `KeyWrapAlgorithm` elementy z element nejvyšší úrovně v rámci RVNÍ, pokud jsou přítomny uvnitř `SecondaryParameters` elementu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Připojí `SecondaryParameters` element odchozí RVNÍ ponechat beze změny.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Vztah důvěryhodnosti RP únor 2005 a vztah důvěryhodnosti služby tokenů zabezpečení 1.3  
 Obsahuje následující prvky v jazyce WSDL pro RP `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Konfigurační soubor klienta obsahuje seznam parametrů.  
  
 Z konfiguračního souboru klienta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nelze rozlišit mezi parametry klienta a služby. Proto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] převede všechny parametry do oboru názvů verze 1.3 vztah důvěryhodnosti.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obslužné rutiny `KeyType`, `KeySize`, a `TokenType` elementy následujícím způsobem:  
  
-   Stáhnout schématu WSDL, vytvoření vazby a přiřaďte `KeyType`, `KeySize`, a `TokenType` RP parametrů. Poté se vytvoří soubor konfigurace klienta.  
  
-   Klient nyní můžete měnit libovolný parametr v konfiguračním souboru.  
  
-   Během doby běhu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zkopíruje všechny parametry zadané `AdditionalTokenParameters` oddíl konfiguračního souboru klienta s výjimkou `KeyType`, `KeySize` a `TokenType`, protože tyto parametry jsou pozornost během konfigurace generování souboru.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>Vztah důvěryhodnosti RP 1.3 a vztah důvěryhodnosti služby tokenů zabezpečení únor 2005  
 Obsahuje následující prvky v jazyce WSDL pro RP `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Konfigurační soubor klienta obsahuje `secondaryParamters` element, který zabalí parametry určeného RP.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zkopíruje všechny parametry zadané v rámci `SecondaryParameters` části RVNÍ element nejvyšší úrovně, ale nelze je převést na obor názvů WS-Trust 2005.
