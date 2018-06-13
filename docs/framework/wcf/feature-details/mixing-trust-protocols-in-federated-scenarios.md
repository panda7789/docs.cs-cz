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
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="8eb9b-102">Smíšené používání protokolů Trust ve federovaných scénářích</span><span class="sxs-lookup"><span data-stu-id="8eb9b-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="8eb9b-103">Mohou existovat scénáře ve kterých federované klienti komunikují se službou a tokenu služby zabezpečení (STS), které nemají stejnou verzi vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="8eb9b-104">Služby mohou obsahovat WSDL `RequestSecurityTokenTemplate` assertion WS-Trust elementy, které jsou různé verze než Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="8eb9b-105">V takových případech klienta Windows Communication Foundation (WCF) převede WS-Trust elementy přijal od `RequestSecurityTokenTemplate` tak, aby odpovídaly Služba tokenů zabezpečení důvěřovat verze.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="8eb9b-106">WCF zpracovává verze neodpovídající důvěryhodnosti pouze pro standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="8eb9b-107">Všechny standardní algoritmus parametry, které jsou rozpoznáno WCF jsou součástí standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="8eb9b-108">Toto téma popisuje chování WCF pomocí různých nastavení důvěryhodnosti mezi službou a služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="8eb9b-109">RP únor 2005 a služby tokenů zabezpečení únor 2005</span><span class="sxs-lookup"><span data-stu-id="8eb9b-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="8eb9b-110">WSDL pro předávající strany (RP) obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="8eb9b-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="8eb9b-111">Konfigurační soubor klienta obsahuje seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="8eb9b-112">WCF nelze rozlišit mezi klientem a službou parametry; Přidá všechny parametry a odešle je v `RequestSecurityTokenTemplate` (RVNÍ).</span><span class="sxs-lookup"><span data-stu-id="8eb9b-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="8eb9b-113">Vztah důvěryhodnosti RP 1.3 a vztah důvěryhodnosti služby tokenů zabezpečení 1.3</span><span class="sxs-lookup"><span data-stu-id="8eb9b-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="8eb9b-114">WSDL pro RP obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="8eb9b-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="8eb9b-115">Konfigurační soubor klienta obsahuje `secondaryParameters` element, který zabalí parametry určeného RP.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="8eb9b-116">Odebere WCF `EncryptionAlgorithm`, `CanonicalizationAlgorithm` a `KeyWrapAlgorithm` elementy z element nejvyšší úrovně v rámci RVNÍ, pokud jsou přítomny uvnitř `SecondaryParameters` elementu.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="8eb9b-117">Připojí WCF `SecondaryParameters` element odchozí RVNÍ ponechat beze změny.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="8eb9b-118">Vztah důvěryhodnosti RP únor 2005 a vztah důvěryhodnosti služby tokenů zabezpečení 1.3</span><span class="sxs-lookup"><span data-stu-id="8eb9b-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="8eb9b-119">Obsahuje následující prvky v jazyce WSDL pro RP `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="8eb9b-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="8eb9b-120">Konfigurační soubor klienta obsahuje seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="8eb9b-121">Z konfiguračního souboru klienta WCF nelze rozlišit parametry klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="8eb9b-122">Proto WCF převede všechny parametry do oboru názvů verze 1.3 vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="8eb9b-123">Obslužné rutiny WCF `KeyType`, `KeySize`, a `TokenType` elementy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8eb9b-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="8eb9b-124">Stáhnout schématu WSDL, vytvoření vazby a přiřaďte `KeyType`, `KeySize`, a `TokenType` RP parametrů.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="8eb9b-125">Poté se vytvoří soubor konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="8eb9b-126">Klient nyní můžete měnit libovolný parametr v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="8eb9b-127">Během doby běhu, WCF zkopíruje všechny parametry zadané `AdditionalTokenParameters` oddíl konfiguračního souboru klienta s výjimkou `KeyType`, `KeySize` a `TokenType`, protože tyto parametry jsou pozornost během konfiguračního souboru generování.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="8eb9b-128">Vztah důvěryhodnosti RP 1.3 a vztah důvěryhodnosti služby tokenů zabezpečení únor 2005</span><span class="sxs-lookup"><span data-stu-id="8eb9b-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="8eb9b-129">Obsahuje následující prvky v jazyce WSDL pro RP `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="8eb9b-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="8eb9b-130">Konfigurační soubor klienta obsahuje `secondaryParamters` element, který zabalí parametry určeného RP.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="8eb9b-131">WCF zkopíruje všechny parametry zadané v rámci `SecondaryParameters` části RVNÍ element nejvyšší úrovně, ale nelze je převést na obor názvů WS-Trust 2005.</span><span class="sxs-lookup"><span data-stu-id="8eb9b-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
