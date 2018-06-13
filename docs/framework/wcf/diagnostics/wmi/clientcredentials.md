---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: aa852ff82c44a3b5009dbc70e1067face44cbbe9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486373"
---
# <a name="clientcredentials"></a><span data-ttu-id="8057c-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="8057c-102">ClientCredentials</span></span>
<span data-ttu-id="8057c-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="8057c-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8057c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8057c-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="8057c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8057c-105">Methods</span></span>  
 <span data-ttu-id="8057c-106">Třída ClientCredentials nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="8057c-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8057c-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8057c-107">Properties</span></span>  
 <span data-ttu-id="8057c-108">Třída ClientCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8057c-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="8057c-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="8057c-109">ClientCertificate</span></span>  
 <span data-ttu-id="8057c-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8057c-110">Data type: string</span></span>  
  
 <span data-ttu-id="8057c-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8057c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8057c-112">Certifikát X.509 klienta používá k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="8057c-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="8057c-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="8057c-113">HttpDigest</span></span>  
 <span data-ttu-id="8057c-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8057c-114">Data type: string</span></span>  
  
 <span data-ttu-id="8057c-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8057c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8057c-116">Aktuální pověření Http Digest.</span><span class="sxs-lookup"><span data-stu-id="8057c-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="8057c-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="8057c-117">IssuedToken</span></span>  
 <span data-ttu-id="8057c-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8057c-118">Data type: string</span></span>  
  
 <span data-ttu-id="8057c-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8057c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8057c-120">Adresa koncového bodu a vazba použitá ke kontaktování služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8057c-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="8057c-121">sdílené</span><span class="sxs-lookup"><span data-stu-id="8057c-121">Peer</span></span>  
 <span data-ttu-id="8057c-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8057c-122">Data type: string</span></span>  
  
 <span data-ttu-id="8057c-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8057c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8057c-124">Pověření, které používá uzlu druhé strany ke svému ověření do dalších uzlů v mřížce.</span><span class="sxs-lookup"><span data-stu-id="8057c-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="8057c-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="8057c-125">ServiceCertificate</span></span>  
 <span data-ttu-id="8057c-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8057c-126">Data type: string</span></span>  
  
 <span data-ttu-id="8057c-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8057c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8057c-128">Certifikát X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="8057c-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="8057c-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="8057c-129">SupportInteractive</span></span>  
 <span data-ttu-id="8057c-130">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="8057c-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="8057c-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8057c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8057c-132">Logická hodnota, která určuje, zda pověření podporuje interaktivní vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="8057c-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="8057c-133">UserName</span><span class="sxs-lookup"><span data-stu-id="8057c-133">UserName</span></span>  
 <span data-ttu-id="8057c-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8057c-134">Data type: string</span></span>  
  
 <span data-ttu-id="8057c-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8057c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8057c-136">Uživatelské jméno a heslo, které klient používá k ověření samotné služby.</span><span class="sxs-lookup"><span data-stu-id="8057c-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="8057c-137">Windows</span><span class="sxs-lookup"><span data-stu-id="8057c-137">Windows</span></span>  
 <span data-ttu-id="8057c-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8057c-138">Data type: string</span></span>  
  
 <span data-ttu-id="8057c-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8057c-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8057c-140">Přihlašovací údaje windows používá klienta ke svému ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="8057c-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8057c-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8057c-141">Requirements</span></span>  
  
|<span data-ttu-id="8057c-142">MOF</span><span class="sxs-lookup"><span data-stu-id="8057c-142">MOF</span></span>|<span data-ttu-id="8057c-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8057c-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8057c-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8057c-144">Namespace</span></span>|<span data-ttu-id="8057c-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8057c-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8057c-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="8057c-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
