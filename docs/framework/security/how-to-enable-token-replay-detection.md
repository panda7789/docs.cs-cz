---
title: "Postupy: Povolení rozpoznání opětovného přehrání tokenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: cde32407f072f3d29af4a8d1aae559e46057ae3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="e61b0-102">Postupy: Povolení rozpoznání opětovného přehrání tokenu</span><span class="sxs-lookup"><span data-stu-id="e61b0-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="e61b0-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="e61b0-103">Applies To</span></span>  
  
-   <span data-ttu-id="e61b0-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="e61b0-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="e61b0-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="e61b0-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e61b0-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e61b0-106">Summary</span></span>  
 <span data-ttu-id="e61b0-107">Tento postup obsahuje podrobné podrobné postupy pro povolení rozpoznání opětovného přehrání tokenu v aplikaci ASP.NET, která používá technologii WIF.</span><span class="sxs-lookup"><span data-stu-id="e61b0-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="e61b0-108">Poskytuje také pokyny, jak otestovat aplikace a ověřte, zda je povoleno rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="e61b0-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="e61b0-109">Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="e61b0-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="e61b0-110">Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="e61b0-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="e61b0-111">Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="e61b0-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="e61b0-112">Ho můžete stáhnout z následujícího umístění: [identita a přístup](http://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="e61b0-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="e61b0-113">Obsah</span><span class="sxs-lookup"><span data-stu-id="e61b0-113">Contents</span></span>  
  
-   <span data-ttu-id="e61b0-114">Cíle</span><span class="sxs-lookup"><span data-stu-id="e61b0-114">Objectives</span></span>  
  
-   <span data-ttu-id="e61b0-115">Přehled</span><span class="sxs-lookup"><span data-stu-id="e61b0-115">Overview</span></span>  
  
-   <span data-ttu-id="e61b0-116">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="e61b0-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e61b0-117">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolte rozpoznání opětovného přehrání</span><span class="sxs-lookup"><span data-stu-id="e61b0-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="e61b0-118">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="e61b0-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="e61b0-119">Cíle</span><span class="sxs-lookup"><span data-stu-id="e61b0-119">Objectives</span></span>  
  
-   <span data-ttu-id="e61b0-120">Vytvořit jednoduchou aplikaci ASP.NET, která používá WIF a vývoj služby tokenů zabezpečení z Identity a přístup</span><span class="sxs-lookup"><span data-stu-id="e61b0-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="e61b0-121">Povolení rozpoznání opětovného přehrání tokenu a ověření, že funguje</span><span class="sxs-lookup"><span data-stu-id="e61b0-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e61b0-122">Přehled</span><span class="sxs-lookup"><span data-stu-id="e61b0-122">Overview</span></span>  
 <span data-ttu-id="e61b0-123">Opakování útoku nastane, když se klient pokouší ověření předávající strany k tokenu služby tokenů zabezpečení, který klient se již používá.</span><span class="sxs-lookup"><span data-stu-id="e61b0-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="e61b0-124">Aby se zabránilo tento útok, obsahuje WIF mezipaměť zjištění opětovného přehrání dřív použité tokeny služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e61b0-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="e61b0-125">Když je povolené, rozpoznání opětovného přehrání tokenu příchozího požadavku zkontroluje a ověřuje, zda je token dřív používal.</span><span class="sxs-lookup"><span data-stu-id="e61b0-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="e61b0-126">Pokud token je již používán, žádost byla odmítnuta a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e61b0-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="e61b0-127">Následující kroky ukazují změny konfigurace vyžaduje, aby se povolilo rozpoznání opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="e61b0-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="e61b0-128">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="e61b0-128">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e61b0-129">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolte rozpoznání opětovného přehrání</span><span class="sxs-lookup"><span data-stu-id="e61b0-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="e61b0-130">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="e61b0-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="e61b0-131">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolte rozpoznání opětovného přehrání</span><span class="sxs-lookup"><span data-stu-id="e61b0-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="e61b0-132">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravit *Web.config* souboru, aby se povolilo rozpoznání opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="e61b0-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e61b0-133">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e61b0-133">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="e61b0-134">Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e61b0-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="e61b0-135">V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="e61b0-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="e61b0-136">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="e61b0-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="e61b0-137">Klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="e61b0-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="e61b0-138">**Identit a přístupu** se zobrazí v okně.</span><span class="sxs-lookup"><span data-stu-id="e61b0-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="e61b0-139">V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="e61b0-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="e61b0-140">Přidejte následující  **\<tokenReplayDetection >** elementu, který chcete *Web.config* okamžitě následující konfigurační soubor  **\<system.identityModel >** a  **\<identityConfiguration >** elementy, zobrazí:</span><span class="sxs-lookup"><span data-stu-id="e61b0-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="e61b0-141">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="e61b0-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="e61b0-142">V tomto kroku budete testovat aplikace ASP.NET WIF povoleno ověření, že je povoleno rozpoznání opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="e61b0-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="e61b0-143">K testování aplikace WIF technologie ASP.NET pro rozpoznání opětovného přehrání</span><span class="sxs-lookup"><span data-stu-id="e61b0-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1.  <span data-ttu-id="e61b0-144">Spuštění řešení stisknutím **F5** klíč.</span><span class="sxs-lookup"><span data-stu-id="e61b0-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="e61b0-145">Můžete by měl mít výchozí domovskou stránku ASP.NET a automaticky k ověření pomocí uživatelského jména *Terry*, což je výchozí uživatel, který je vrácena službou tokenů zabezpečení vývoj.</span><span class="sxs-lookup"><span data-stu-id="e61b0-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="e61b0-146">V prohlížeči stiskněte **zpět** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e61b0-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="e61b0-147">By se měla zobrazit s **chyba serveru v aplikaci '/'** stránky s popisem následující: *ID1062: opětovného přehrání zjištěna: tokenu: 'System.IdentityModel.Tokens.SamlSecurityToken'* , za nímž následuje *AssertionId* a *vystavitele*.</span><span class="sxs-lookup"><span data-stu-id="e61b0-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="e61b0-148">Tato chybová stránka se zobrazuje, protože k výjimce typu <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> se vyvolá, když byla zjištěna opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="e61b0-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="e61b0-149">K této chybě dojde, protože se pokoušíte znovu odešle počáteční požadavek POST při token byl nejdříve.</span><span class="sxs-lookup"><span data-stu-id="e61b0-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="e61b0-150">**Zpět** tlačítko nezpůsobí toto chování na následné požadavky na server.</span><span class="sxs-lookup"><span data-stu-id="e61b0-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
