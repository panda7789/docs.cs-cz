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
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="c2a32-102">Smíšené používání protokolů Trust ve federovaných scénářích</span><span class="sxs-lookup"><span data-stu-id="c2a32-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="c2a32-103">Mohou existovat scénáře ve kterých federované klienti komunikují se službou a tokenu služby zabezpečení (STS), které nemají stejnou verzi vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="c2a32-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="c2a32-104">Služby mohou obsahovat WSDL `RequestSecurityTokenTemplate` assertion WS-Trust elementy, které jsou různé verze než Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c2a32-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="c2a32-105">V takových případech [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] převede WS-Trust elementy přijaté z klienta `RequestSecurityTokenTemplate` tak, aby odpovídaly Služba tokenů zabezpečení důvěřovat verze.</span><span class="sxs-lookup"><span data-stu-id="c2a32-105">In such cases, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c2a32-106">obslužné rutiny neshoda verze důvěryhodnosti pouze pro standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="c2a32-106"> handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="c2a32-107">Všechny standardní algoritmus parametry, které jsou rozpoznáno [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou součástí standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="c2a32-107">All standard algorithm parameters that are recognized by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are part of the standard binding.</span></span> <span data-ttu-id="c2a32-108">Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chování s různými důvěřovat nastavení mezi služba a služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c2a32-108">This topic describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="c2a32-109">RP únor 2005 a služby tokenů zabezpečení únor 2005</span><span class="sxs-lookup"><span data-stu-id="c2a32-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="c2a32-110">WSDL pro předávající strany (RP) obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="c2a32-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="c2a32-111">Konfigurační soubor klienta obsahuje seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="c2a32-111">The client configuration file contains a list of parameters.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c2a32-112">nelze rozlišit mezi klientem a službou parametry; Přidá všechny parametry a odešle je v `RequestSecurityTokenTemplate` (RVNÍ).</span><span class="sxs-lookup"><span data-stu-id="c2a32-112"> cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="c2a32-113">Vztah důvěryhodnosti RP 1.3 a vztah důvěryhodnosti služby tokenů zabezpečení 1.3</span><span class="sxs-lookup"><span data-stu-id="c2a32-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="c2a32-114">WSDL pro RP obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="c2a32-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="c2a32-115">Konfigurační soubor klienta obsahuje `secondaryParameters` element, který zabalí parametry určeného RP.</span><span class="sxs-lookup"><span data-stu-id="c2a32-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c2a32-116">Odebere `EncryptionAlgorithm`, `CanonicalizationAlgorithm` a `KeyWrapAlgorithm` elementy z element nejvyšší úrovně v rámci RVNÍ, pokud jsou přítomny uvnitř `SecondaryParameters` elementu.</span><span class="sxs-lookup"><span data-stu-id="c2a32-116"> removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c2a32-117">Připojí `SecondaryParameters` element odchozí RVNÍ ponechat beze změny.</span><span class="sxs-lookup"><span data-stu-id="c2a32-117"> appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="c2a32-118">Vztah důvěryhodnosti RP únor 2005 a vztah důvěryhodnosti služby tokenů zabezpečení 1.3</span><span class="sxs-lookup"><span data-stu-id="c2a32-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="c2a32-119">Obsahuje následující prvky v jazyce WSDL pro RP `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="c2a32-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="c2a32-120">Konfigurační soubor klienta obsahuje seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="c2a32-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="c2a32-121">Z konfiguračního souboru klienta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nelze rozlišit mezi parametry klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="c2a32-121">From the client configuration file, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="c2a32-122">Proto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] převede všechny parametry do oboru názvů verze 1.3 vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="c2a32-122">Therefore [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c2a32-123">obslužné rutiny `KeyType`, `KeySize`, a `TokenType` elementy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c2a32-123"> handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="c2a32-124">Stáhnout schématu WSDL, vytvoření vazby a přiřaďte `KeyType`, `KeySize`, a `TokenType` RP parametrů.</span><span class="sxs-lookup"><span data-stu-id="c2a32-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="c2a32-125">Poté se vytvoří soubor konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="c2a32-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="c2a32-126">Klient nyní můžete měnit libovolný parametr v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c2a32-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="c2a32-127">Během doby běhu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zkopíruje všechny parametry zadané `AdditionalTokenParameters` oddíl konfiguračního souboru klienta s výjimkou `KeyType`, `KeySize` a `TokenType`, protože tyto parametry jsou pozornost během konfigurace generování souboru.</span><span class="sxs-lookup"><span data-stu-id="c2a32-127">During runtime, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="c2a32-128">Vztah důvěryhodnosti RP 1.3 a vztah důvěryhodnosti služby tokenů zabezpečení únor 2005</span><span class="sxs-lookup"><span data-stu-id="c2a32-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="c2a32-129">Obsahuje následující prvky v jazyce WSDL pro RP `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="c2a32-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="c2a32-130">Konfigurační soubor klienta obsahuje `secondaryParamters` element, který zabalí parametry určeného RP.</span><span class="sxs-lookup"><span data-stu-id="c2a32-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c2a32-131">zkopíruje všechny parametry zadané v rámci `SecondaryParameters` části RVNÍ element nejvyšší úrovně, ale nelze je převést na obor názvů WS-Trust 2005.</span><span class="sxs-lookup"><span data-stu-id="c2a32-131"> copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
