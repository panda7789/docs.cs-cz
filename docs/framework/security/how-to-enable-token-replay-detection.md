---
title: 'Postupy: Povolení zjišťování opakování tokenů'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
ms.openlocfilehash: 0149bf424751a0c95337743b02465629826d9686
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625850"
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="99e4b-102">Postupy: Povolení zjišťování opakování tokenů</span><span class="sxs-lookup"><span data-stu-id="99e4b-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="99e4b-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="99e4b-103">Applies To</span></span>  
  
- <span data-ttu-id="99e4b-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="99e4b-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="99e4b-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="99e4b-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="99e4b-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="99e4b-106">Summary</span></span>  
 <span data-ttu-id="99e4b-107">Tento návod obsahuje podrobně popisuje postupy pro povolení rozpoznání opětovného přehrání tokenu v aplikaci ASP.NET, která pomocí technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="99e4b-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="99e4b-108">Také poskytuje pokyny k otestování aplikace ověřit, zda je povoleno rozpoznání opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="99e4b-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="99e4b-109">Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="99e4b-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="99e4b-110">Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="99e4b-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="99e4b-111">Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="99e4b-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="99e4b-112">Můžete ho stáhnout z následujícího umístění: [Nástroj identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="99e4b-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="99e4b-113">Obsah</span><span class="sxs-lookup"><span data-stu-id="99e4b-113">Contents</span></span>  
  
- <span data-ttu-id="99e4b-114">Cíle</span><span class="sxs-lookup"><span data-stu-id="99e4b-114">Objectives</span></span>  
  
- <span data-ttu-id="99e4b-115">Přehled</span><span class="sxs-lookup"><span data-stu-id="99e4b-115">Overview</span></span>  
  
- <span data-ttu-id="99e4b-116">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="99e4b-116">Summary of Steps</span></span>  
  
- <span data-ttu-id="99e4b-117">Krok 1 – Vytvoření jednoduché technologie ASP.NET webové formuláře aplikace a povolení zjišťování opakování</span><span class="sxs-lookup"><span data-stu-id="99e4b-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
- <span data-ttu-id="99e4b-118">Krok 2 – otestování řešení</span><span class="sxs-lookup"><span data-stu-id="99e4b-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="99e4b-119">Cíle</span><span class="sxs-lookup"><span data-stu-id="99e4b-119">Objectives</span></span>  
  
- <span data-ttu-id="99e4b-120">Vytvořit jednoduchou aplikaci ASP.NET, která používá technologie WIF a služba STS pro vývoj od Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="99e4b-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
- <span data-ttu-id="99e4b-121">Povolení rozpoznání opětovného přehrání tokenu a ověření, že je funkční</span><span class="sxs-lookup"><span data-stu-id="99e4b-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="99e4b-122">Přehled</span><span class="sxs-lookup"><span data-stu-id="99e4b-122">Overview</span></span>  
 <span data-ttu-id="99e4b-123">Opakování útoku nastane, pokud klient pokus o ověření k předávající straně s tokenem služby tokenů zabezpečení, které už klient použil.</span><span class="sxs-lookup"><span data-stu-id="99e4b-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="99e4b-124">Aby se zabránilo útoku, obsahuje technologie WIF mezipaměti zjišťování opakování předchozích tokenů služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="99e4b-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="99e4b-125">Pokud povolená, rozpoznání opětovného přehrání ověří token příchozího požadavku a ověří, zda token, který byl dříve používali.</span><span class="sxs-lookup"><span data-stu-id="99e4b-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="99e4b-126">Pokud token, který se už používá, žádost byla odmítnuta a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="99e4b-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="99e4b-127">Následující kroky ukazují, změny konfigurace, které jsou nutné k povolení zjišťování opakování.</span><span class="sxs-lookup"><span data-stu-id="99e4b-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="99e4b-128">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="99e4b-128">Summary of Steps</span></span>  
  
- <span data-ttu-id="99e4b-129">Krok 1 – Vytvoření jednoduché technologie ASP.NET webové formuláře aplikace a povolení zjišťování opakování</span><span class="sxs-lookup"><span data-stu-id="99e4b-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
- <span data-ttu-id="99e4b-130">Krok 2 – otestování řešení</span><span class="sxs-lookup"><span data-stu-id="99e4b-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="99e4b-131">Krok 1 – Vytvoření jednoduché technologie ASP.NET webové formuláře aplikace a povolení zjišťování opakování</span><span class="sxs-lookup"><span data-stu-id="99e4b-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="99e4b-132">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravit *Web.config* souboru k povolení zjišťování opakování.</span><span class="sxs-lookup"><span data-stu-id="99e4b-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="99e4b-133">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="99e4b-133">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="99e4b-134">Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="99e4b-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="99e4b-135">V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="99e4b-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="99e4b-136">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="99e4b-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="99e4b-137">Klikněte pravým tlačítkem myši **TestApp** projektu v rámci **Průzkumníku řešení**a pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="99e4b-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5. <span data-ttu-id="99e4b-138">**Identit a přístupu** zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="99e4b-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="99e4b-139">V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="99e4b-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6. <span data-ttu-id="99e4b-140">Přidejte následující  **\<tokenReplayDetection >** elementu *Web.config* bezprostředně následující konfigurační soubor  **\<system.identityModel >** a  **\<identityConfiguration >** prvky, jako jsou zobrazeny:</span><span class="sxs-lookup"><span data-stu-id="99e4b-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="99e4b-141">Krok 2 – otestování řešení</span><span class="sxs-lookup"><span data-stu-id="99e4b-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="99e4b-142">V tomto kroku otestujete aplikaci technologie ASP.NET s podporou technologie WIF ověřit, že byl povolen rozpoznání opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="99e4b-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="99e4b-143">Chcete-li otestovat aplikaci technologie ASP.NET s podporou technologie WIF pro rozpoznání opětovného přehrání</span><span class="sxs-lookup"><span data-stu-id="99e4b-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1. <span data-ttu-id="99e4b-144">Spuštění řešení stisknutím kombinace kláves **F5** klíč.</span><span class="sxs-lookup"><span data-stu-id="99e4b-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="99e4b-145">Měli byste se výchozí domovskou stránku ASP.NET a automaticky ověřuje se uživatelské jméno *Terry*, což je výchozí uživatel, který je vrácen služba STS pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="99e4b-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2. <span data-ttu-id="99e4b-146">Stiskněte v prohlížeči **zpět** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="99e4b-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="99e4b-147">Mělo by se zobrazit pomocí **chyba serveru v aplikaci '/'** stránky s popisem následující: *ID1062: Byl zjištěn opakování pro: token: "System.IdentityModel.Tokens.samlsecuritytoken tak"* následovaný *AssertionId* a *vystavitele*.</span><span class="sxs-lookup"><span data-stu-id="99e4b-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="99e4b-148">Tato chybová stránka se zobrazuje, protože výjimku typu <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> byla vyvolána, když byla zjištěna opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="99e4b-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="99e4b-149">K této chybě dochází, protože se pokoušíte znovu poslat počáteční požadavek POST převedou token, který byl poprvé.</span><span class="sxs-lookup"><span data-stu-id="99e4b-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="99e4b-150">**Zpět** tlačítko nezpůsobí toto chování o následných požadavcích na server.</span><span class="sxs-lookup"><span data-stu-id="99e4b-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
