---
title: Smíšené používání protokolů Trust ve federovaných scénářích
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: ce5c3a1875d84d98068dcc78d8346a88bc0b28f3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182904"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="c8b53-102">Smíšené používání protokolů Trust ve federovaných scénářích</span><span class="sxs-lookup"><span data-stu-id="c8b53-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="c8b53-103">Můžou existovat scénáře, ve kterých federované klienti komunikují se službou a Token služby zabezpečení (STS), které nemají stejnou verzi vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="c8b53-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="c8b53-104">Služby mohou obsahovat WSDL `RequestSecurityTokenTemplate` kontrolní výraz se WS-Trust prvky, které jsou z různých verzí než Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c8b53-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="c8b53-105">V takovém případě klienta Windows Communication Foundation (WCF) převede prvky WS-Trust poslal `RequestSecurityTokenTemplate` tak, aby odpovídaly Služba tokenů zabezpečení důvěryhodnosti verze.</span><span class="sxs-lookup"><span data-stu-id="c8b53-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="c8b53-106">WCF se stará verze neodpovídající důvěryhodnosti pouze pro standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="c8b53-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="c8b53-107">Všechny standardní algoritmus parametry, které jsou rozpoznány modulem WCF jsou součástí standardní vazbu.</span><span class="sxs-lookup"><span data-stu-id="c8b53-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="c8b53-108">Toto téma popisuje chování WCF pomocí různých nastavení vztahu důvěryhodnosti mezi službou a služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c8b53-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="c8b53-109">RP únor 2005 a služba tokenů zabezpečení únor 2005</span><span class="sxs-lookup"><span data-stu-id="c8b53-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="c8b53-110">WSDL pro předávající strany (RP) obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="c8b53-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="c8b53-111">Klient konfigurační soubor obsahuje seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="c8b53-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="c8b53-112">WCF nelze rozlišit mezi klientem a službou parametry; Přidá všechny parametry a odesílá je `RequestSecurityTokenTemplate` (RVNÍ).</span><span class="sxs-lookup"><span data-stu-id="c8b53-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="c8b53-113">Vztah důvěryhodnosti předávající strany 1.3 a služba tokenů zabezpečení důvěryhodnosti 1.3</span><span class="sxs-lookup"><span data-stu-id="c8b53-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="c8b53-114">Rozhraní jazyka WSDL pro poskytovatele prostředků obsahuje následující prvky v rámci `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="c8b53-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="c8b53-115">Obsahuje konfigurační soubor klienta `secondaryParameters` element, který obtéká parametry určené RP.</span><span class="sxs-lookup"><span data-stu-id="c8b53-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="c8b53-116">Odebere WCF `EncryptionAlgorithm`, `CanonicalizationAlgorithm` a `KeyWrapAlgorithm` prvky z element nejvyšší úrovně v rámci RVNÍ, pokud jsou přítomné uvnitř `SecondaryParameters` elementu.</span><span class="sxs-lookup"><span data-stu-id="c8b53-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="c8b53-117">Připojí WCF `SecondaryParameters` – element pro odchozí RVNÍ ponechat beze změny.</span><span class="sxs-lookup"><span data-stu-id="c8b53-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="c8b53-118">1.3 vztah důvěryhodnosti předávající strany Trust Únor 2005 a služba tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c8b53-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="c8b53-119">Obsahuje následující prvky v rozhraní jazyka WSDL pro RP `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="c8b53-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="c8b53-120">Klient konfigurační soubor obsahuje seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="c8b53-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="c8b53-121">Ze souboru konfigurace klienta WCF nelze rozlišovat mezi parametry klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="c8b53-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="c8b53-122">WCF proto převede všechny parametry do oboru názvů verze 1.3 vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="c8b53-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="c8b53-123">Obslužné rutiny WCF `KeyType`, `KeySize`, a `TokenType` prvky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c8b53-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="c8b53-124">Stáhněte si jazyka WSDL, vytvoření vazby a přiřaďte `KeyType`, `KeySize`, a `TokenType` z parametrů předávající strany.</span><span class="sxs-lookup"><span data-stu-id="c8b53-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="c8b53-125">Pak bude vygenerován soubor konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="c8b53-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="c8b53-126">Klient nyní můžete měnit žádné parametry v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c8b53-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="c8b53-127">Za běhu, WCF, zkopíruje všechny parametry zadané pro `AdditionalTokenParameters` souboru konfigurace klientů s výjimkou `KeyType`, `KeySize` a `TokenType`, protože tyto parametry jsou zahrnuté během konfiguračního souboru generování.</span><span class="sxs-lookup"><span data-stu-id="c8b53-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="c8b53-128">Vztah důvěryhodnosti předávající strany 1.3 a služba tokenů zabezpečení důvěryhodnosti únor 2005</span><span class="sxs-lookup"><span data-stu-id="c8b53-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="c8b53-129">Obsahuje následující prvky v rozhraní jazyka WSDL pro RP `RequestSecurityTokenTemplate` části:</span><span class="sxs-lookup"><span data-stu-id="c8b53-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="c8b53-130">Obsahuje konfigurační soubor klienta `secondaryParamters` element, který obtéká parametry určené RP.</span><span class="sxs-lookup"><span data-stu-id="c8b53-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="c8b53-131">Zkopíruje všechny parametry zadané v rámci WCF `SecondaryParameters` části RVNÍ element nejvyšší úrovně, ale nelze je převést na obor názvů WS-Trust 2005.</span><span class="sxs-lookup"><span data-stu-id="c8b53-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
