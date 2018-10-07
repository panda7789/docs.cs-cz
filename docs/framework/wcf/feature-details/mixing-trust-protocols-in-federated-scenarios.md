---
title: Smíšené používání protokolů Trust ve federovaných scénářích
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
ms.openlocfilehash: d4290880d8d708811a95b38356aa61f0d23c89a8
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842499"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Smíšené používání protokolů Trust ve federovaných scénářích
Můžou existovat scénáře, ve kterých federované klienti komunikují se službou a Token služby zabezpečení (STS), které nemají stejnou verzi vztah důvěryhodnosti. Služby mohou obsahovat WSDL `RequestSecurityTokenTemplate` kontrolní výraz se WS-Trust prvky, které jsou z různých verzí než Služba tokenů zabezpečení. V takovém případě klienta Windows Communication Foundation (WCF) převede prvky WS-Trust poslal `RequestSecurityTokenTemplate` tak, aby odpovídaly Služba tokenů zabezpečení důvěryhodnosti verze. WCF se stará verze neodpovídající důvěryhodnosti pouze pro standardní vazby. Všechny standardní algoritmus parametry, které jsou rozpoznány modulem WCF jsou součástí standardní vazbu. Toto téma popisuje chování WCF pomocí různých nastavení vztahu důvěryhodnosti mezi službou a služba tokenů zabezpečení.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP únor 2005 a služba tokenů zabezpečení únor 2005  
 WSDL pro předávající strany (RP) obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Klient konfigurační soubor obsahuje seznam parametrů.  
  
 WCF nelze rozlišit mezi klientem a službou parametry; Přidá všechny parametry a odesílá je `RequestSecurityTokenTemplate` (RVNÍ).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>Vztah důvěryhodnosti předávající strany 1.3 a služba tokenů zabezpečení důvěryhodnosti 1.3  
 Rozhraní jazyka WSDL pro poskytovatele prostředků obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Obsahuje konfigurační soubor klienta `secondaryParameters` element, který obtéká parametry určené RP.  
  
 Odebere WCF `EncryptionAlgorithm`, `CanonicalizationAlgorithm` a `KeyWrapAlgorithm` prvky z element nejvyšší úrovně v rámci RVNÍ, pokud jsou přítomné uvnitř `SecondaryParameters` elementu. Připojí WCF `SecondaryParameters` – element pro odchozí RVNÍ ponechat beze změny.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>1.3 vztah důvěryhodnosti předávající strany Trust Únor 2005 a služba tokenů zabezpečení  
 Obsahuje následující prvky v rozhraní jazyka WSDL pro RP `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Klient konfigurační soubor obsahuje seznam parametrů.  
  
 Ze souboru konfigurace klienta WCF nelze rozlišovat mezi parametry klienta a služby. WCF proto převede všechny parametry do oboru názvů verze 1.3 vztah důvěryhodnosti.  
  
 Obslužné rutiny WCF `KeyType`, `KeySize`, a `TokenType` prvky následujícím způsobem:  
  
-   Stáhněte si jazyka WSDL, vytvoření vazby a přiřaďte `KeyType`, `KeySize`, a `TokenType` z parametrů předávající strany. Pak bude vygenerován soubor konfigurace klienta.  
  
-   Klient nyní můžete měnit žádné parametry v konfiguračním souboru.  
  
-   Za běhu, WCF, zkopíruje všechny parametry zadané pro `AdditionalTokenParameters` souboru konfigurace klientů s výjimkou `KeyType`, `KeySize` a `TokenType`, protože tyto parametry jsou zahrnuté během konfiguračního souboru generování.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>Vztah důvěryhodnosti předávající strany 1.3 a služba tokenů zabezpečení důvěryhodnosti únor 2005  
 Obsahuje následující prvky v rozhraní jazyka WSDL pro RP `RequestSecurityTokenTemplate` části:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Obsahuje konfigurační soubor klienta `secondaryParamters` element, který obtéká parametry určené RP.  
  
 Zkopíruje všechny parametry zadané v rámci WCF `SecondaryParameters` části RVNÍ element nejvyšší úrovně, ale nelze je převést na obor názvů WS-Trust 2005.
