---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771202"
---
# <a name="clientcredentials"></a><span data-ttu-id="4d04a-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="4d04a-102">ClientCredentials</span></span>
<span data-ttu-id="4d04a-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="4d04a-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d04a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d04a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4d04a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4d04a-105">Methods</span></span>  
 <span data-ttu-id="4d04a-106">Třída ClientCredentials nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4d04a-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4d04a-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4d04a-107">Properties</span></span>  
 <span data-ttu-id="4d04a-108">Třída ClientCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4d04a-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="4d04a-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="4d04a-109">ClientCertificate</span></span>  
 <span data-ttu-id="4d04a-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4d04a-110">Data type: string</span></span>  
  
 <span data-ttu-id="4d04a-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d04a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d04a-112">Certifikát X.509 klienta používá k ověření ve službě.</span><span class="sxs-lookup"><span data-stu-id="4d04a-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="4d04a-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="4d04a-113">HttpDigest</span></span>  
 <span data-ttu-id="4d04a-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4d04a-114">Data type: string</span></span>  
  
 <span data-ttu-id="4d04a-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d04a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d04a-116">Aktuální pověření Http Digest.</span><span class="sxs-lookup"><span data-stu-id="4d04a-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="4d04a-117">Třídy IssuedToken</span><span class="sxs-lookup"><span data-stu-id="4d04a-117">IssuedToken</span></span>  
 <span data-ttu-id="4d04a-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4d04a-118">Data type: string</span></span>  
  
 <span data-ttu-id="4d04a-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d04a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d04a-120">Adresa koncového bodu a vazba použitá ke kontaktování služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4d04a-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="4d04a-121">Peer</span><span class="sxs-lookup"><span data-stu-id="4d04a-121">Peer</span></span>  
 <span data-ttu-id="4d04a-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4d04a-122">Data type: string</span></span>  
  
 <span data-ttu-id="4d04a-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d04a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d04a-124">Přihlašovací údaje, které bude rovnocenný uzel používá ke svému ověření do jiných uzlů v mřížce.</span><span class="sxs-lookup"><span data-stu-id="4d04a-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="4d04a-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="4d04a-125">ServiceCertificate</span></span>  
 <span data-ttu-id="4d04a-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4d04a-126">Data type: string</span></span>  
  
 <span data-ttu-id="4d04a-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d04a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d04a-128">Certifikát služby X.509.</span><span class="sxs-lookup"><span data-stu-id="4d04a-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="4d04a-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="4d04a-129">SupportInteractive</span></span>  
 <span data-ttu-id="4d04a-130">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="4d04a-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="4d04a-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d04a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d04a-132">Logická hodnota určující, zda přihlašovací údaje, které podporuje interaktivní vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="4d04a-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="4d04a-133">UserName</span><span class="sxs-lookup"><span data-stu-id="4d04a-133">UserName</span></span>  
 <span data-ttu-id="4d04a-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4d04a-134">Data type: string</span></span>  
  
 <span data-ttu-id="4d04a-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d04a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d04a-136">Uživatelské jméno a heslo, které klient použije ke svému ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="4d04a-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="4d04a-137">Windows</span><span class="sxs-lookup"><span data-stu-id="4d04a-137">Windows</span></span>  
 <span data-ttu-id="4d04a-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4d04a-138">Data type: string</span></span>  
  
 <span data-ttu-id="4d04a-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d04a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d04a-140">Pověření systému windows používá klient ke svému ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="4d04a-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d04a-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d04a-141">Requirements</span></span>  
  
|<span data-ttu-id="4d04a-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="4d04a-142">MOF</span></span>|<span data-ttu-id="4d04a-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4d04a-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4d04a-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4d04a-144">Namespace</span></span>|<span data-ttu-id="4d04a-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4d04a-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d04a-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d04a-146">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
