---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 8b6200f84f352d49cf142d9c8b97d1c2b36149b2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180897"
---
# <a name="clientcredentials"></a><span data-ttu-id="07781-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="07781-102">ClientCredentials</span></span>
<span data-ttu-id="07781-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="07781-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07781-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07781-104">Syntax</span></span>  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="07781-105">Metody</span><span class="sxs-lookup"><span data-stu-id="07781-105">Methods</span></span>  
 <span data-ttu-id="07781-106">Třída ClientCredentials nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="07781-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="07781-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="07781-107">Properties</span></span>  
 <span data-ttu-id="07781-108">Třída ClientCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="07781-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="07781-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="07781-109">ClientCertificate</span></span>  
 <span data-ttu-id="07781-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="07781-110">Data type: string</span></span>  
  
 <span data-ttu-id="07781-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="07781-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07781-112">Certifikát X.509 klienta používá k ověření ve službě.</span><span class="sxs-lookup"><span data-stu-id="07781-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="07781-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="07781-113">HttpDigest</span></span>  
 <span data-ttu-id="07781-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="07781-114">Data type: string</span></span>  
  
 <span data-ttu-id="07781-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="07781-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07781-116">Aktuální pověření Http Digest.</span><span class="sxs-lookup"><span data-stu-id="07781-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="07781-117">Třídy IssuedToken</span><span class="sxs-lookup"><span data-stu-id="07781-117">IssuedToken</span></span>  
 <span data-ttu-id="07781-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="07781-118">Data type: string</span></span>  
  
 <span data-ttu-id="07781-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="07781-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07781-120">Adresa koncového bodu a vazba použitá ke kontaktování služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="07781-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="07781-121">Peer</span><span class="sxs-lookup"><span data-stu-id="07781-121">Peer</span></span>  
 <span data-ttu-id="07781-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="07781-122">Data type: string</span></span>  
  
 <span data-ttu-id="07781-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="07781-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07781-124">Přihlašovací údaje, které bude rovnocenný uzel používá ke svému ověření do jiných uzlů v mřížce.</span><span class="sxs-lookup"><span data-stu-id="07781-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="07781-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="07781-125">ServiceCertificate</span></span>  
 <span data-ttu-id="07781-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="07781-126">Data type: string</span></span>  
  
 <span data-ttu-id="07781-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="07781-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07781-128">Certifikát služby X.509.</span><span class="sxs-lookup"><span data-stu-id="07781-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="07781-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="07781-129">SupportInteractive</span></span>  
 <span data-ttu-id="07781-130">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="07781-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="07781-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="07781-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07781-132">Logická hodnota určující, zda přihlašovací údaje, které podporuje interaktivní vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="07781-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="07781-133">UserName</span><span class="sxs-lookup"><span data-stu-id="07781-133">UserName</span></span>  
 <span data-ttu-id="07781-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="07781-134">Data type: string</span></span>  
  
 <span data-ttu-id="07781-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="07781-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07781-136">Uživatelské jméno a heslo, které klient použije ke svému ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="07781-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="07781-137">Windows</span><span class="sxs-lookup"><span data-stu-id="07781-137">Windows</span></span>  
 <span data-ttu-id="07781-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="07781-138">Data type: string</span></span>  
  
 <span data-ttu-id="07781-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="07781-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07781-140">Pověření systému windows používá klient ke svému ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="07781-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07781-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07781-141">Requirements</span></span>  
  
|<span data-ttu-id="07781-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="07781-142">MOF</span></span>|<span data-ttu-id="07781-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="07781-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="07781-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="07781-144">Namespace</span></span>|<span data-ttu-id="07781-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="07781-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07781-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="07781-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
