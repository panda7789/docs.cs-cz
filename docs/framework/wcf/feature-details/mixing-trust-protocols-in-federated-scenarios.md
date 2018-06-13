---
title: Smíšené používání protokolů Trust ve federovaných scénářích
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bca23ba16c69c6d21ed7cf49aaebb8d2ed079f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494456"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Smíšené používání protokolů Trust ve federovaných scénářích
Mohou existovat scénáře ve kterých federované klienti komunikují se službou a tokenu služby zabezpečení (STS), které nemají stejnou verzi vztah důvěryhodnosti. Služby mohou obsahovat WSDL `RequestSecurityTokenTemplate` assertion WS-Trust elementy, které jsou různé verze než Služba tokenů zabezpečení. V takových případech klienta Windows Communication Foundation (WCF) převede WS-Trust elementy přijal od `RequestSecurityTokenTemplate` tak, aby odpovídaly Služba tokenů zabezpečení důvěřovat verze. WCF zpracovává verze neodpovídající důvěryhodnosti pouze pro standardní vazby. Všechny standardní algoritmus parametry, které jsou rozpoznáno WCF jsou součástí standardní vazby. Toto téma popisuje chování WCF pomocí různých nastavení důvěryhodnosti mezi službou a služba tokenů zabezpečení.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP únor 2005 a služby tokenů zabezpečení únor 2005  
 WSDL pro předávající strany (RP) obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Konfigurační soubor klienta obsahuje seznam parametrů.  
  
 WCF nelze rozlišit mezi klientem a službou parametry; Přidá všechny parametry a odešle je v `RequestSecurityTokenTemplate` (RVNÍ).  
  
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
  
 Odebere WCF `EncryptionAlgorithm`, `CanonicalizationAlgorithm` a `KeyWrapAlgorithm` elementy z element nejvyšší úrovně v rámci RVNÍ, pokud jsou přítomny uvnitř `SecondaryParameters` elementu. Připojí WCF `SecondaryParameters` element odchozí RVNÍ ponechat beze změny.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Vztah důvěryhodnosti RP únor 2005 a vztah důvěryhodnosti služby tokenů zabezpečení 1.3  
 Obsahuje následující prvky v jazyce WSDL pro RP `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Konfigurační soubor klienta obsahuje seznam parametrů.  
  
 Z konfiguračního souboru klienta WCF nelze rozlišit parametry klienta a služby. Proto WCF převede všechny parametry do oboru názvů verze 1.3 vztah důvěryhodnosti.  
  
 Obslužné rutiny WCF `KeyType`, `KeySize`, a `TokenType` elementy následujícím způsobem:  
  
-   Stáhnout schématu WSDL, vytvoření vazby a přiřaďte `KeyType`, `KeySize`, a `TokenType` RP parametrů. Poté se vytvoří soubor konfigurace klienta.  
  
-   Klient nyní můžete měnit libovolný parametr v konfiguračním souboru.  
  
-   Během doby běhu, WCF zkopíruje všechny parametry zadané `AdditionalTokenParameters` oddíl konfiguračního souboru klienta s výjimkou `KeyType`, `KeySize` a `TokenType`, protože tyto parametry jsou pozornost během konfiguračního souboru generování.  
  
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
  
 WCF zkopíruje všechny parametry zadané v rámci `SecondaryParameters` části RVNÍ element nejvyšší úrovně, ale nelze je převést na obor názvů WS-Trust 2005.
