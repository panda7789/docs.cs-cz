---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6fba00dc98f6b5525e1cb9588ed52bc483a665e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clientcredentials"></a><span data-ttu-id="f76f2-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="f76f2-102">ClientCredentials</span></span>
<span data-ttu-id="f76f2-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="f76f2-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f76f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f76f2-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f76f2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f76f2-105">Methods</span></span>  
 <span data-ttu-id="f76f2-106">Třída ClientCredentials nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f76f2-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f76f2-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f76f2-107">Properties</span></span>  
 <span data-ttu-id="f76f2-108">Třída ClientCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f76f2-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="f76f2-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="f76f2-109">ClientCertificate</span></span>  
 <span data-ttu-id="f76f2-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f76f2-110">Data type: string</span></span>  
  
 <span data-ttu-id="f76f2-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f76f2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76f2-112">Certifikát X.509 klienta používá k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="f76f2-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="f76f2-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="f76f2-113">HttpDigest</span></span>  
 <span data-ttu-id="f76f2-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f76f2-114">Data type: string</span></span>  
  
 <span data-ttu-id="f76f2-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f76f2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76f2-116">Aktuální pověření Http Digest.</span><span class="sxs-lookup"><span data-stu-id="f76f2-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="f76f2-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="f76f2-117">IssuedToken</span></span>  
 <span data-ttu-id="f76f2-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f76f2-118">Data type: string</span></span>  
  
 <span data-ttu-id="f76f2-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f76f2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76f2-120">Adresa koncového bodu a vazba použitá ke kontaktování služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f76f2-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="f76f2-121">sdílené</span><span class="sxs-lookup"><span data-stu-id="f76f2-121">Peer</span></span>  
 <span data-ttu-id="f76f2-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f76f2-122">Data type: string</span></span>  
  
 <span data-ttu-id="f76f2-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f76f2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76f2-124">Pověření, které používá uzlu druhé strany ke svému ověření do dalších uzlů v mřížce.</span><span class="sxs-lookup"><span data-stu-id="f76f2-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="f76f2-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="f76f2-125">ServiceCertificate</span></span>  
 <span data-ttu-id="f76f2-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f76f2-126">Data type: string</span></span>  
  
 <span data-ttu-id="f76f2-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f76f2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76f2-128">Certifikát X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="f76f2-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="f76f2-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="f76f2-129">SupportInteractive</span></span>  
 <span data-ttu-id="f76f2-130">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="f76f2-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="f76f2-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f76f2-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76f2-132">Logická hodnota, která určuje, zda pověření podporuje interaktivní vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="f76f2-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="f76f2-133">UserName</span><span class="sxs-lookup"><span data-stu-id="f76f2-133">UserName</span></span>  
 <span data-ttu-id="f76f2-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f76f2-134">Data type: string</span></span>  
  
 <span data-ttu-id="f76f2-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f76f2-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76f2-136">Uživatelské jméno a heslo, které klient používá k ověření samotné služby.</span><span class="sxs-lookup"><span data-stu-id="f76f2-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="f76f2-137">Windows</span><span class="sxs-lookup"><span data-stu-id="f76f2-137">Windows</span></span>  
 <span data-ttu-id="f76f2-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f76f2-138">Data type: string</span></span>  
  
 <span data-ttu-id="f76f2-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f76f2-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76f2-140">Přihlašovací údaje windows používá klienta ke svému ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="f76f2-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f76f2-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f76f2-141">Requirements</span></span>  
  
|<span data-ttu-id="f76f2-142">MOF</span><span class="sxs-lookup"><span data-stu-id="f76f2-142">MOF</span></span>|<span data-ttu-id="f76f2-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f76f2-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f76f2-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f76f2-144">Namespace</span></span>|<span data-ttu-id="f76f2-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f76f2-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f76f2-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="f76f2-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
