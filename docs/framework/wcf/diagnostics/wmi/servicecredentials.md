---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230925"
---
# <a name="servicecredentials"></a><span data-ttu-id="77ae6-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="77ae6-102">ServiceCredentials</span></span>
<span data-ttu-id="77ae6-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="77ae6-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ae6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77ae6-104">Syntax</span></span>  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="77ae6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="77ae6-105">Methods</span></span>  
 <span data-ttu-id="77ae6-106">Třídu ServiceCredentials nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="77ae6-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="77ae6-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="77ae6-107">Properties</span></span>  
 <span data-ttu-id="77ae6-108">Třídu ServiceCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="77ae6-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="77ae6-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="77ae6-109">ClientCertificate</span></span>  
 <span data-ttu-id="77ae6-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="77ae6-110">Data type: string</span></span>  
  
 <span data-ttu-id="77ae6-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="77ae6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77ae6-112">Certifikát ověření a opatření nastavení klienta pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="77ae6-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="77ae6-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="77ae6-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="77ae6-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="77ae6-114">Data type: string</span></span>  
  
 <span data-ttu-id="77ae6-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="77ae6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77ae6-116">Aktuálně vydaného tokenu ověřování nastavení pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="77ae6-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="77ae6-117">Peer</span><span class="sxs-lookup"><span data-stu-id="77ae6-117">Peer</span></span>  
 <span data-ttu-id="77ae6-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="77ae6-118">Data type: string</span></span>  
  
 <span data-ttu-id="77ae6-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="77ae6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77ae6-120">Aktuální pověření ověřování a zřizování nastavení používané koncových bodů přenosu stejné.</span><span class="sxs-lookup"><span data-stu-id="77ae6-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="77ae6-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="77ae6-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="77ae6-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="77ae6-122">Data type: string</span></span>  
  
 <span data-ttu-id="77ae6-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="77ae6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77ae6-124">Určuje aktuální nastavení zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="77ae6-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="77ae6-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="77ae6-125">ServiceCertificate</span></span>  
 <span data-ttu-id="77ae6-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="77ae6-126">Data type: string</span></span>  
  
 <span data-ttu-id="77ae6-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="77ae6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77ae6-128">Platnost certifikátu spojeného s touto službou.</span><span class="sxs-lookup"><span data-stu-id="77ae6-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="77ae6-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="77ae6-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="77ae6-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="77ae6-130">Data type: string</span></span>  
  
 <span data-ttu-id="77ae6-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="77ae6-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77ae6-132">Nastavení uživatelského jména a hesla pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="77ae6-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="77ae6-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="77ae6-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="77ae6-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="77ae6-134">Data type: string</span></span>  
  
 <span data-ttu-id="77ae6-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="77ae6-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77ae6-136">Nastavení ověřování Windows pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="77ae6-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77ae6-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77ae6-137">Requirements</span></span>  
  
|<span data-ttu-id="77ae6-138">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="77ae6-138">MOF</span></span>|<span data-ttu-id="77ae6-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="77ae6-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="77ae6-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="77ae6-140">Namespace</span></span>|<span data-ttu-id="77ae6-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="77ae6-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77ae6-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77ae6-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
