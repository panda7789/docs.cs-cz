---
title: Nástroj Configuration Editor (SvcConfigEditor.exe)
description: Přečtěte si, jak spravovat nastavení vazeb WCF, chování, služeb a diagnostiky pomocí editoru konfigurace služby WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 258437ff616b969d40feabbfff364ad2cc6b25bc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247646"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="147b7-103">Nástroj Configuration Editor (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="147b7-103">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>

<span data-ttu-id="147b7-104">Editor konfigurací služby Windows Communication Foundation (WCF) (SvcConfigEditor.exe) umožňuje správcům a vývojářům vytvářet a upravovat nastavení konfigurace služeb WCF pomocí grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="147b7-104">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="147b7-105">Pomocí tohoto nástroje můžete spravovat nastavení vazeb WCF, chování, služeb a diagnostiky, aniž byste museli přímo upravovat konfigurační soubory XML.</span><span class="sxs-lookup"><span data-stu-id="147b7-105">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>

<span data-ttu-id="147b7-106">Editor konfigurace služby najdete ve složce C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span><span class="sxs-lookup"><span data-stu-id="147b7-106">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>

## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="147b7-107">Editor konfigurace WCF</span><span class="sxs-lookup"><span data-stu-id="147b7-107">The WCF Configuration Editor</span></span>

<span data-ttu-id="147b7-108">Editor konfigurace služby se dodává s průvodcem, který vás provede všemi kroky v části Konfigurace služby WCF nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="147b7-108">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="147b7-109">Důrazně doporučujeme použít Průvodce místo toho přímo v editoru.</span><span class="sxs-lookup"><span data-stu-id="147b7-109">You are strongly advised to use the wizard instead of the editor directly.</span></span>

<span data-ttu-id="147b7-110">Pokud už máte nějaké konfigurační soubory, které vyhovují schématu Standard System.Configuration, můžete spravovat konkrétní nastavení pro vazby, chování, služby a diagnostiku s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="147b7-110">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="147b7-111">Editor konfigurace služby umožňuje spravovat nastavení pro existující konfigurační soubory WCF i spustitelné soubory, služby modelu COM+ a služby hostované na webu.</span><span class="sxs-lookup"><span data-stu-id="147b7-111">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="147b7-112">Při otevírání služby hostované na webu pomocí editoru konfigurace služby se zobrazí jak vlastní konfigurace služby, tak zděděné konfigurace uzlů nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="147b7-112">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>

<span data-ttu-id="147b7-113">Vzhledem k tomu, že nastavení konfigurace WCF jsou umístěna v `<system.serviceModel>` části konfiguračního souboru, Editor pracuje výhradně s obsahem tohoto prvku a nepřistupuje k ostatním prvkům ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-113">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="147b7-114">Můžete přímo přejít na existující konfigurační soubory nebo můžete vybrat sestavení, které obsahuje službu, virtuální adresář nebo službu COM+.</span><span class="sxs-lookup"><span data-stu-id="147b7-114">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="147b7-115">Editor načte konfigurační soubor pro danou službu a umožní uživateli buď přidat nové prvky, nebo upravit existující prvky vnořené v `<system.serviceModel>` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-115">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>

<span data-ttu-id="147b7-116">Editor podporuje technologii IntelliSense a vynutil dodržování předpisů schématu.</span><span class="sxs-lookup"><span data-stu-id="147b7-116">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="147b7-117">Výsledný výstup je zaručený v dodržení schématu konfiguračního souboru a má syntakticky správné hodnoty dat.</span><span class="sxs-lookup"><span data-stu-id="147b7-117">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="147b7-118">Editor však nezaručuje, že konfigurační soubor je sémanticky platný.</span><span class="sxs-lookup"><span data-stu-id="147b7-118">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="147b7-119">Jinými slovy Editor nezaručuje, že konfigurační soubor může spolupracovat se službou, kterou konfiguruje.</span><span class="sxs-lookup"><span data-stu-id="147b7-119">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>

> [!CAUTION]
> <span data-ttu-id="147b7-120">Editor nemůže po úpravě elementu odstranit konfigurační prvek z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-120">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="147b7-121">Pokud například použijete editor k nastavení názvu koncového bodu na neprázdný řetězec a uložíte ho, konfigurační soubor má následující obsah, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="147b7-121">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> <span data-ttu-id="147b7-122">Pokud se pokusíte odebrat název nastavením na prázdný řetězec a uložit soubor, konfigurační soubor stále obsahuje `name` atribut, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="147b7-122">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> <span data-ttu-id="147b7-123">Chcete-li tento atribut vyprázdnit, je nutné ručně upravit element pomocí jiného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="147b7-123">To purge the attribute, you must manually edit the element using another text editor.</span></span>
>
> <span data-ttu-id="147b7-124">Pokud použijete `issueToken` prvek chování koncového bodu, měli byste být obzvláště opatrní u tohoto problému `clientCredential` .</span><span class="sxs-lookup"><span data-stu-id="147b7-124">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="147b7-125">Konkrétně `address` atribut jeho `localIssuer` dílčího elementu nesmí být prázdným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="147b7-125">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="147b7-126">Pokud jste změnili `address` atribut pomocí editoru konfigurace a chcete ho úplně odebrat, měli byste použít jiný nástroj než Editor.</span><span class="sxs-lookup"><span data-stu-id="147b7-126">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="147b7-127">V opačném případě atribut obsahuje prázdný řetězec a vaše aplikace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="147b7-127">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>

## <a name="using-the-configuration-editor"></a><span data-ttu-id="147b7-128">Použití editoru konfigurace</span><span class="sxs-lookup"><span data-stu-id="147b7-128">Using the Configuration Editor</span></span>

<span data-ttu-id="147b7-129">Editor konfigurací služby najdete v následujících Windows SDK umístění instalace:</span><span class="sxs-lookup"><span data-stu-id="147b7-129">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>

<span data-ttu-id="147b7-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="147b7-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>

<span data-ttu-id="147b7-131">Po spuštění editoru konfigurace služby můžete pomocí nabídky **soubor/otevřít** vyhledat službu nebo sestavení, které chcete spravovat.</span><span class="sxs-lookup"><span data-stu-id="147b7-131">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="147b7-132">Můžete otevřít konfigurační soubory přímo, vyhledat WCF/COM + Services a otevřít konfigurační soubory pro služby hostované na webu.</span><span class="sxs-lookup"><span data-stu-id="147b7-132">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>

<span data-ttu-id="147b7-133">Uživatelské rozhraní editoru konfigurace služby je rozdělené do následujících oblastí:</span><span class="sxs-lookup"><span data-stu-id="147b7-133">The Service Configuration Editor's user interface is divided into the following areas:</span></span>

- <span data-ttu-id="147b7-134">Podokno stromového zobrazení, které zobrazuje prvky konfigurace ve stromové struktuře vlevo.</span><span class="sxs-lookup"><span data-stu-id="147b7-134">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="147b7-135">Kliknutím pravým tlačítkem myši na uzly můžete provádět operace ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="147b7-135">You can perform operations in the tree by right-clicking the nodes.</span></span>

- <span data-ttu-id="147b7-136">Podokno úloh, které zobrazuje běžné úkoly pro aktuální prvky v levém dolním rohu okna</span><span class="sxs-lookup"><span data-stu-id="147b7-136">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>

- <span data-ttu-id="147b7-137">Podokno podrobností, které zobrazuje podrobné nastavení uzlu Konfigurace vybraného ve stromovém zobrazení vpravo.</span><span class="sxs-lookup"><span data-stu-id="147b7-137">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>

### <a name="opening-a-configuration-file"></a><span data-ttu-id="147b7-138">Otevření konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="147b7-138">Opening a Configuration File</span></span>

1. <span data-ttu-id="147b7-139">Spusťte editor konfigurace služby pomocí příkazového řádku a přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe` .</span><span class="sxs-lookup"><span data-stu-id="147b7-139">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="147b7-140">V nabídce **soubor** vyberte **otevřít** a klikněte na typ souboru, který chcete spravovat.</span><span class="sxs-lookup"><span data-stu-id="147b7-140">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>

3. <span data-ttu-id="147b7-141">V dialogovém okně **otevřít** přejděte na konkrétní soubor, který chcete spravovat, a dvakrát na něj klikněte.</span><span class="sxs-lookup"><span data-stu-id="147b7-141">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>

<span data-ttu-id="147b7-142">Prohlížeč automaticky sleduje cestu sloučení konfigurace a vytvoří zobrazení sloučené konfigurace.</span><span class="sxs-lookup"><span data-stu-id="147b7-142">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="147b7-143">Například vlastní konfigurace nehostované služby je kombinací Machine.config a App.config. Všechny změny se aplikují na aktivní soubor v SvcConfigEditor.</span><span class="sxs-lookup"><span data-stu-id="147b7-143">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="147b7-144">Pokud chcete upravit konkrétní soubor v cestě pro sloučení konfigurace, měli byste ho otevřít přímo.</span><span class="sxs-lookup"><span data-stu-id="147b7-144">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>

> [!NOTE]
> <span data-ttu-id="147b7-145">Editor konfigurací znovu načte aktuálně otevřený konfigurační soubor, když byl druhý upravený mimo editor.</span><span class="sxs-lookup"><span data-stu-id="147b7-145">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="147b7-146">Pokud k tomu dojde, všechny změny, které nejsou uložené v editoru trvale, se ztratí.</span><span class="sxs-lookup"><span data-stu-id="147b7-146">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="147b7-147">Pokud probíhá opětovné načítání konzistentně, nejpravděpodobnější příčinou je služba, která nepřetržitě přistupuje ke konfiguračnímu souboru, například antivirový software spuštěný na pozadí.</span><span class="sxs-lookup"><span data-stu-id="147b7-147">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="147b7-148">Chcete-li tento problém vyřešit, zajistěte, aby byl Editor konfigurací jediným procesem, který má přístup k souboru při jeho otevření.</span><span class="sxs-lookup"><span data-stu-id="147b7-148">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>

### <a name="services"></a><span data-ttu-id="147b7-149">Služby</span><span class="sxs-lookup"><span data-stu-id="147b7-149">Services</span></span>

<span data-ttu-id="147b7-150">Uzel **služby** zobrazí všechny služby, které jsou aktuálně přiřazeny k konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-150">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="147b7-151">Každý dílčí uzel ve stromové struktuře odpovídá dílčímu elementu <`services`> elementu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-151">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>

<span data-ttu-id="147b7-152">Když kliknete na uzel **služby** , můžete zobrazit nebo provádět úlohy na stránce Souhrn služby v podokně **podrobností** .</span><span class="sxs-lookup"><span data-stu-id="147b7-152">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>

#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="147b7-153">Vytváří se nová konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="147b7-153">Creating a new Service Configuration</span></span>

<span data-ttu-id="147b7-154">Novou konfiguraci služby můžete vytvořit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="147b7-154">You can create a new service configuration in the following ways:</span></span>

- <span data-ttu-id="147b7-155">Pomocí Průvodce: klikněte na odkaz **vytvořit novou službu...**</span><span class="sxs-lookup"><span data-stu-id="147b7-155">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="147b7-156">na stránce podokno úloh nebo souhrn spusťte průvodce.</span><span class="sxs-lookup"><span data-stu-id="147b7-156">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="147b7-157">Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="147b7-157">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="147b7-158">Ruční vytvoření: můžete kliknout pravým tlačítkem myši na uzel **služby** a vybrat možnost **Nová služba**.</span><span class="sxs-lookup"><span data-stu-id="147b7-158">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>

#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="147b7-159">Vytváří se nová konfigurace koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="147b7-159">Creating a new Service Endpoint Configuration</span></span>

<span data-ttu-id="147b7-160">Novou konfiguraci koncového bodu služby můžete vytvořit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="147b7-160">You can create a new service endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="147b7-161">Vytvořit pomocí Průvodce: klikněte na odkaz **vytvořit nový koncový bod služby...**</span><span class="sxs-lookup"><span data-stu-id="147b7-161">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="147b7-162">na stránce podokno úloh nebo souhrn spusťte průvodce.</span><span class="sxs-lookup"><span data-stu-id="147b7-162">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="147b7-163">Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="147b7-163">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="147b7-164">Vytvořit ručně: po vytvoření služby můžete kliknout pravým tlačítkem myši na uzel **koncové body** a zvolit**Nový koncový bod služby**.</span><span class="sxs-lookup"><span data-stu-id="147b7-164">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>

#### <a name="editing-a-service-configuration"></a><span data-ttu-id="147b7-165">Úprava konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="147b7-165">Editing a Service Configuration</span></span>

1. <span data-ttu-id="147b7-166">Klikněte na uzel **služby** .</span><span class="sxs-lookup"><span data-stu-id="147b7-166">Click a **Service** node.</span></span>

2. <span data-ttu-id="147b7-167">Upravte nastavení v Gridech vlastností.</span><span class="sxs-lookup"><span data-stu-id="147b7-167">Edit the settings in the property grids.</span></span>

#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="147b7-168">Úprava konfigurace koncového bodu služby</span><span class="sxs-lookup"><span data-stu-id="147b7-168">Editing a Service Endpoint Configuration</span></span>

1. <span data-ttu-id="147b7-169">Klikněte na uzel **koncového bodu služby** .</span><span class="sxs-lookup"><span data-stu-id="147b7-169">Click a **Service Endpoint** node.</span></span>

2. <span data-ttu-id="147b7-170">Upravte nastavení v Gridech vlastností.</span><span class="sxs-lookup"><span data-stu-id="147b7-170">Edit the settings in the property grids.</span></span>

#### <a name="adding-a-base-address"></a><span data-ttu-id="147b7-171">Přidání základní adresy</span><span class="sxs-lookup"><span data-stu-id="147b7-171">Adding a Base Address</span></span>

1. <span data-ttu-id="147b7-172">Klikněte na uzel **hostitele** .</span><span class="sxs-lookup"><span data-stu-id="147b7-172">Click the **Host** node.</span></span>

2. <span data-ttu-id="147b7-173">Klikněte na **Nový...**</span><span class="sxs-lookup"><span data-stu-id="147b7-173">Click the **New…**</span></span> <span data-ttu-id="147b7-174">tlačítko v části **základní adresy** .</span><span class="sxs-lookup"><span data-stu-id="147b7-174">button in the **Base Addresses** section.</span></span>

3. <span data-ttu-id="147b7-175">Do dialogového okna zadejte identifikátor URI základní adresy.</span><span class="sxs-lookup"><span data-stu-id="147b7-175">Type in the base address URI in the dialog box.</span></span>

4. <span data-ttu-id="147b7-176">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="147b7-176">Click **OK**.</span></span>

> [!NOTE]
> <span data-ttu-id="147b7-177">V [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) rámci tohoto nástroje nelze upravit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="147b7-177">You cannot edit the value of [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="147b7-178">Chcete-li přidat nebo upravit tento prvek, měli byste použít textový editor nebo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="147b7-178">To add or modify this element, you should use a text editor or Visual Studio.</span></span>

### <a name="client"></a><span data-ttu-id="147b7-179">Klient</span><span class="sxs-lookup"><span data-stu-id="147b7-179">Client</span></span>

<span data-ttu-id="147b7-180">Uzel **klienta** zobrazí všechny koncové body klienta v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-180">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="147b7-181">Každý dílčí uzel ve stromové struktuře odpovídá dílčímu elementu <`client`> elementu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-181">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>

<span data-ttu-id="147b7-182">Po kliknutí na uzel **klienta** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** klienta v **podokně podrobností**.</span><span class="sxs-lookup"><span data-stu-id="147b7-182">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="147b7-183">Vytváří se nová konfigurace koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="147b7-183">Creating a new Client Endpoint Configuration</span></span>

<span data-ttu-id="147b7-184">Novou konfiguraci koncového bodu klienta můžete vytvořit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="147b7-184">You can create a new client endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="147b7-185">Průvodce vytvořením: kliknutím na odkaz **vytvořit nového klienta...**</span><span class="sxs-lookup"><span data-stu-id="147b7-185">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="147b7-186">v **podokně úloh** v levém dolním rohu okna nebo **souhrnu** spusťte průvodce.</span><span class="sxs-lookup"><span data-stu-id="147b7-186">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="147b7-187">Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="147b7-187">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="147b7-188">Průvodce vás vyzve, abyste odkazovali na umístění konfigurace služby, ze které se vygenerovala konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="147b7-188">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="147b7-189">Pak můžete zvolit koncový bod služby, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="147b7-189">You can then choose the service endpoint to connect to.</span></span>

- <span data-ttu-id="147b7-190">Ruční vytvoření: klikněte pravým tlačítkem na uzel **koncové body** v části **klient**a vyberte **Nový koncový bod klienta**.</span><span class="sxs-lookup"><span data-stu-id="147b7-190">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>

#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="147b7-191">Úprava konfigurace koncového bodu klienta</span><span class="sxs-lookup"><span data-stu-id="147b7-191">Editing a Client Endpoint Configuration</span></span>

1. <span data-ttu-id="147b7-192">Klikněte na uzel **koncového bodu klienta** .</span><span class="sxs-lookup"><span data-stu-id="147b7-192">Click a **Client Endpoint** node.</span></span>

2. <span data-ttu-id="147b7-193">Upravte nastavení v Gridech vlastností.</span><span class="sxs-lookup"><span data-stu-id="147b7-193">Edit the settings in the property grids.</span></span>

### <a name="standard-endpoint"></a><span data-ttu-id="147b7-194">Standardní koncový bod</span><span class="sxs-lookup"><span data-stu-id="147b7-194">Standard Endpoint</span></span>

<span data-ttu-id="147b7-195">Standardní koncové body jsou specializované koncové body, které mají jednu nebo více aspektů adresy, kontraktu a vazby nastavené na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="147b7-195">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>

<span data-ttu-id="147b7-196">Taková nastavení konfigurace se ukládají do uzlu **standardního koncového bodu** .</span><span class="sxs-lookup"><span data-stu-id="147b7-196">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="147b7-197">Uzel **standardního koncového bodu** zobrazí všechna nastavení standardního koncového bodu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-197">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="147b7-198">Každý dílčí uzel ve stromové struktuře odpovídá dílčímu prvku v `<standardEndpoints>` elementu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-198">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>

<span data-ttu-id="147b7-199">Když kliknete na uzel **standardního koncového bodu** , můžete zobrazit nebo provádět úlohy na **stránce Souhrn** standardního koncového bodu v **podokně podrobností**.</span><span class="sxs-lookup"><span data-stu-id="147b7-199">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="147b7-200">Vytváří se nová konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="147b7-200">Creating a New Standard Endpoint Configuration</span></span>

<span data-ttu-id="147b7-201">Novou konfiguraci standardního koncového bodu můžete vytvořit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="147b7-201">You can create a new standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="147b7-202">Klikněte pravým tlačítkem na uzel **standardní koncový bod** a vyberte **Nová konfigurace standardního koncového bodu...**</span><span class="sxs-lookup"><span data-stu-id="147b7-202">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="147b7-203">V dialogovém okně vyberte typ vazby a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="147b7-203">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="147b7-204">Vyberte uzel **standardního koncového bodu** a klikněte na **nový standardní konfigurace koncového bodu...**</span><span class="sxs-lookup"><span data-stu-id="147b7-204">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="147b7-205">v **podokně úloh** v levém dolním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="147b7-205">in the **Task Pane** on the lower-left of the window.</span></span>

<span data-ttu-id="147b7-206">Zobrazí se dialogové okno **Vytvoření nového standardního koncového bodu** , ve kterém jsou uvedeny všechny registrované standardní typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="147b7-206">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="147b7-207">Zobrazení a úprava konfigurace standardního koncového bodu</span><span class="sxs-lookup"><span data-stu-id="147b7-207">Viewing and Editing a Standard Endpoint Configuration</span></span>

<span data-ttu-id="147b7-208">Konfiguraci standardního koncového bodu můžete otevřít pro zobrazení a úpravy následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="147b7-208">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>

- <span data-ttu-id="147b7-209">Kliknutím rozbalte uzel **standardní koncový bod** a klikněte na příslušný dílčí uzel koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="147b7-209">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>

- <span data-ttu-id="147b7-210">Klikněte na uzel **standardní koncový bod** a v podokně podrobností klikněte na příslušný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="147b7-210">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>

<span data-ttu-id="147b7-211">Atributy koncového bodu jsou zobrazeny v pravém podokně pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="147b7-211">Attributes for the endpoint are shown in the right pane for editing.</span></span>

#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="147b7-212">Odstraňuje se konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="147b7-212">Deleting a Standard Endpoint Configuration</span></span>

<span data-ttu-id="147b7-213">Konfiguraci standardních koncových bodů můžete odstranit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="147b7-213">You can delete a standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="147b7-214">Kliknutím rozbalte uzel **standardní koncový bod** a klikněte pravým tlačítkem myši na příslušný dílčí uzel koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="147b7-214">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="147b7-215">K odstranění koncového bodu použijte kontextový příkaz **Odstranit konfiguraci standardního koncového bodu** .</span><span class="sxs-lookup"><span data-stu-id="147b7-215">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>

- <span data-ttu-id="147b7-216">Klikněte na uzel **standardní koncový bod** .</span><span class="sxs-lookup"><span data-stu-id="147b7-216">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="147b7-217">V podokně **úloh** klikněte na **Odstranit standardní konfiguraci koncového bodu**.</span><span class="sxs-lookup"><span data-stu-id="147b7-217">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>

<span data-ttu-id="147b7-218">Pokud se používá standardní koncový bod, při pokusu o odstranění se zobrazí varovná zpráva: **standardní koncový bod se používá. Pokud ho odstraníte nyní, nezapomeňte odstranit všechny jeho odkazy v jiných částech konfigurace (například v koncovém bodu služby nebo koncovém bodu klienta). V opačném případě bude konfigurace neplatná a nedá se otevřít příště. Opravdu chcete odstranit standardní koncový bod? "**</span><span class="sxs-lookup"><span data-stu-id="147b7-218">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>

### <a name="binding"></a><span data-ttu-id="147b7-219">Vazba</span><span class="sxs-lookup"><span data-stu-id="147b7-219">Binding</span></span>

<span data-ttu-id="147b7-220">Konfigurace vazeb se používají ke konfiguraci vazeb u koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="147b7-220">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="147b7-221">Taková nastavení konfigurace jsou uložena v uzlu **vazby** .</span><span class="sxs-lookup"><span data-stu-id="147b7-221">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="147b7-222">Konfigurace odkazu na koncové body podle názvu a více koncových bodů může odkazovat na konfiguraci jedné vazby.</span><span class="sxs-lookup"><span data-stu-id="147b7-222">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>

<span data-ttu-id="147b7-223">Uzel **vazby** zobrazí všechna nastavení vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-223">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="147b7-224">Každý dílčí uzel ve stromové struktuře odpovídá dílčímu prvku v `bindings` prvku <> v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-224">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>

<span data-ttu-id="147b7-225">Po kliknutí na uzel **vazby** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** vazby v **podokně podrobností**.</span><span class="sxs-lookup"><span data-stu-id="147b7-225">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="147b7-226">Vytváří se nová konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="147b7-226">Creating a New Binding Configuration</span></span>

<span data-ttu-id="147b7-227">Novou konfiguraci vazby můžete vytvořit následujícími způsoby.</span><span class="sxs-lookup"><span data-stu-id="147b7-227">You can create a new binding configuration in the following ways.</span></span>

- <span data-ttu-id="147b7-228">Klikněte pravým tlačítkem myši na uzel **vazby** a vyberte možnost **Nová konfigurace vazby**...</span><span class="sxs-lookup"><span data-stu-id="147b7-228">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="147b7-229">V dialogovém okně vyberte typ vazby a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="147b7-229">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="147b7-230">Vyberte uzel **vazby** a klikněte na **Nová konfigurace vazby**...</span><span class="sxs-lookup"><span data-stu-id="147b7-230">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="147b7-231">v **podokně úloh** v levém dolním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="147b7-231">in the **Task Pane** on the lower-left of the window.</span></span>

- <span data-ttu-id="147b7-232">Na stránce Souhrn služby nebo klienta klikněte na **kliknutím na tlačítko vytvořit** v poli **Konfigurace vazby** vytvořte konfiguraci vazby pro odpovídající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="147b7-232">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="147b7-233">Přidání rozšíření elementu vazby k vlastní vazbě</span><span class="sxs-lookup"><span data-stu-id="147b7-233">Adding Binding Element Extensions to a Custom Binding</span></span>

1. <span data-ttu-id="147b7-234">Vyberte vazbu, do které chcete přidat prvek rozšíření.</span><span class="sxs-lookup"><span data-stu-id="147b7-234">Select the binding you want to add an extension element to.</span></span>

2. <span data-ttu-id="147b7-235">Klikněte na tlačítko **Add** (Přidat).</span><span class="sxs-lookup"><span data-stu-id="147b7-235">Click **Add**.</span></span>

3. <span data-ttu-id="147b7-236">V seznamu dostupných rozšíření vyberte rozšíření prvku vazby, které chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="147b7-236">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="147b7-237">Chcete-li vybrat více položek, stiskněte současně klávesu CTRL.</span><span class="sxs-lookup"><span data-stu-id="147b7-237">To select multiple items, press the CTRL key simultaneously.</span></span>

4. <span data-ttu-id="147b7-238">Klikněte na tlačítko **Add** (Přidat).</span><span class="sxs-lookup"><span data-stu-id="147b7-238">Click **Add**.</span></span>

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="147b7-239">Úprava pozice rozšíření ve vlastní vazbě</span><span class="sxs-lookup"><span data-stu-id="147b7-239">Adjusting the Extension Position in a Custom Binding</span></span>

<span data-ttu-id="147b7-240">Vlastní vazba je kolekce elementů vazby, které tvoří zásobník.</span><span class="sxs-lookup"><span data-stu-id="147b7-240">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="147b7-241">Každý prvek vazby v zásobníku má vlastní nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="147b7-241">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="147b7-242">Pořadí rozšíření prvků vazby ve vlastní vazbě označuje jejich pozice v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="147b7-242">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="147b7-243">Jako první se aplikují prvky v horní části zásobníku.</span><span class="sxs-lookup"><span data-stu-id="147b7-243">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="147b7-244">Postup změny řazení:</span><span class="sxs-lookup"><span data-stu-id="147b7-244">To change the ordering:</span></span>

1. <span data-ttu-id="147b7-245">Vyberte vlastní uzel vazby.</span><span class="sxs-lookup"><span data-stu-id="147b7-245">Select the custom binding node.</span></span>

2. <span data-ttu-id="147b7-246">Vyberte jeden prvek rozšíření vazby v oddílu **pozice rozšíření vazby elementu** .</span><span class="sxs-lookup"><span data-stu-id="147b7-246">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>

3. <span data-ttu-id="147b7-247">Chcete-li změnit pozici vybraného prvku, použijte tlačítko **nahoru** nebo **dolů** na levé straně seznamu.</span><span class="sxs-lookup"><span data-stu-id="147b7-247">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="147b7-248">Úprava konfigurace rozšíření elementu vazby ve vlastní vazbě</span><span class="sxs-lookup"><span data-stu-id="147b7-248">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>

1. <span data-ttu-id="147b7-249">Vyberte uzel vazby ve stromu.</span><span class="sxs-lookup"><span data-stu-id="147b7-249">Select the binding node in the tree.</span></span>

2. <span data-ttu-id="147b7-250">Vyberte vlastní vazbu obsahující prvek, který chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="147b7-250">Select the custom binding that contains the element you want to edit.</span></span>

3. <span data-ttu-id="147b7-251">Vyberte rozšíření prvku vazby, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="147b7-251">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="147b7-252">Nastavení prvku se zobrazí v pravém podokně, kde je lze upravovat.</span><span class="sxs-lookup"><span data-stu-id="147b7-252">The settings of the element appear in the right pane, where they can be edited.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="147b7-253">Diagnostika</span><span class="sxs-lookup"><span data-stu-id="147b7-253">Diagnostics</span></span>

<span data-ttu-id="147b7-254">V uzlu **Diagnostika** se zobrazí všechna nastavení diagnostiky v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-254">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="147b7-255">Umožňuje zapnout nebo vypnout čítače výkonu, povolit nebo zakázat rozhraní WMI (Windows Management Instrumentation) (WMI), nakonfigurovat trasování WCF a nakonfigurovat protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="147b7-255">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="147b7-256">Nastavení v uzlu **Diagnostika** odpovídá `system.diagnostics` oddílu <> a v `<diagnostics>` `<system.serviceModel>` konfiguračním souboru v části.</span><span class="sxs-lookup"><span data-stu-id="147b7-256">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>

<span data-ttu-id="147b7-257">Po kliknutí na uzel **Diagnostika** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** diagnostiky v **podokně podrobností**.</span><span class="sxs-lookup"><span data-stu-id="147b7-257">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="147b7-258">Konfigurace čítačů výkonu a rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="147b7-258">Configuring performance counters and WMI</span></span>

1. <span data-ttu-id="147b7-259">Klikněte na uzel **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="147b7-259">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="147b7-260">Klikněte na **Přepnout čítače výkonu**.</span><span class="sxs-lookup"><span data-stu-id="147b7-260">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="147b7-261">Čítač výkonu má tři stavy: vypnuto (výchozí), ServiceOnly a All.</span><span class="sxs-lookup"><span data-stu-id="147b7-261">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="147b7-262">Kliknutím na odkaz přepnete nastavení mezi těmito třemi stavy.</span><span class="sxs-lookup"><span data-stu-id="147b7-262">Clicking the link toggles the setting among these three states.</span></span>

#### <a name="configuring-wmi-provider"></a><span data-ttu-id="147b7-263">Konfigurace zprostředkovatele rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="147b7-263">Configuring WMI Provider</span></span>

1. <span data-ttu-id="147b7-264">Klikněte na uzel **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="147b7-264">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="147b7-265">Pokud chcete povolit zprostředkovatele rozhraní WMI, klikněte na odkaz **Povolit zprostředkovatele rozhraní WMI** .</span><span class="sxs-lookup"><span data-stu-id="147b7-265">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>

#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="147b7-266">Povolení trasování WCF</span><span class="sxs-lookup"><span data-stu-id="147b7-266">Enabling WCF Tracing</span></span>

<span data-ttu-id="147b7-267">Můžete vytvořit trasovací soubor WCF se standardními vlastnostmi nebo nastavit vlastní trasovací soubor.</span><span class="sxs-lookup"><span data-stu-id="147b7-267">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="147b7-268">Klikněte na uzel **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="147b7-268">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="147b7-269">Klikněte na **Povolit trasování**.</span><span class="sxs-lookup"><span data-stu-id="147b7-269">Click **Enable Tracing**.</span></span>

3. <span data-ttu-id="147b7-270">Kliknutím na odkaz **úroveň trasování** upravíte úroveň trasování.</span><span class="sxs-lookup"><span data-stu-id="147b7-270">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="147b7-271">Existuje šest úrovní trasování: vypnuto, kritická, chyba, upozornění, informace a podrobné.</span><span class="sxs-lookup"><span data-stu-id="147b7-271">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="147b7-272">Možnost **trasování aktivity** a **šíření** aktivity umožňuje použít funkci trasování aktivity WCF.</span><span class="sxs-lookup"><span data-stu-id="147b7-272">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>

4. <span data-ttu-id="147b7-273">Klikněte na název naslouchacího procesu trasování a určete trasovací soubor a možnosti.</span><span class="sxs-lookup"><span data-stu-id="147b7-273">Click the trace listener name to specify the trace file and options.</span></span>

#### <a name="enabling-wcf-logging"></a><span data-ttu-id="147b7-274">Povolení protokolování WCF</span><span class="sxs-lookup"><span data-stu-id="147b7-274">Enabling WCF Logging</span></span>

<span data-ttu-id="147b7-275">Můžete vytvořit trasovací soubor WCF se standardními vlastnostmi nebo nastavit vlastní trasovací soubor.</span><span class="sxs-lookup"><span data-stu-id="147b7-275">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="147b7-276">Klikněte na uzel **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="147b7-276">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="147b7-277">Klikněte na **Povolit protokolování zpráv**.</span><span class="sxs-lookup"><span data-stu-id="147b7-277">Click **Enable Message Logging**.</span></span>

3. <span data-ttu-id="147b7-278">Kliknutím na odkaz **úroveň protokolu** upravíte úroveň protokolu.</span><span class="sxs-lookup"><span data-stu-id="147b7-278">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="147b7-279">Existují tři úrovně protokolu: chybné, služba a přenos.</span><span class="sxs-lookup"><span data-stu-id="147b7-279">There are three log levels: Malformed, Service, and Transport.</span></span>

4. <span data-ttu-id="147b7-280">Klikněte na název naslouchacího procesu a určete soubor protokolu a možnosti.</span><span class="sxs-lookup"><span data-stu-id="147b7-280">Click the listener name to specify the log file and options.</span></span>

> [!NOTE]
> <span data-ttu-id="147b7-281">Pokud chcete, aby se protokoly trasování a zpráv vyprázdny automaticky, když je vaše aplikace zavřená, povolte možnost **automatického vyprázdnit** .</span><span class="sxs-lookup"><span data-stu-id="147b7-281">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>

<span data-ttu-id="147b7-282">**Stránka Souhrn** **diagnostiky** umožňuje provádět nejběžnější úlohy v konfiguraci diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="147b7-282">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="147b7-283">Pokud však chcete ručně upravit nastavení naslouchacího procesu a zdrojů, je nutné rozbalit uzel **Diagnostika** a upravit nastavení v uzlu **protokolování zpráv**, **naslouchací procesy** a **zdroje** .</span><span class="sxs-lookup"><span data-stu-id="147b7-283">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="147b7-284">Povolení vlastního trasování WCF nebo protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="147b7-284">Enabling WCF Custom Tracing or Message Logging</span></span>

1. <span data-ttu-id="147b7-285">Klikněte na uzel **Diagnostika** a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="147b7-285">Click the **Diagnostics** node, and expand it.</span></span>

2. <span data-ttu-id="147b7-286">Klikněte pravým tlačítkem myši na uzel **naslouchací procesy** a vyberte možnost **nový naslouchací proces**.</span><span class="sxs-lookup"><span data-stu-id="147b7-286">Right-click the **Listeners** node and select **New Listener**.</span></span>

3. <span data-ttu-id="147b7-287">Do pole **InitData** zadejte název trasovacího souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-287">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="147b7-288">Můžete kliknout na tlačítko "..." tlačítko pro procházení k cestě.</span><span class="sxs-lookup"><span data-stu-id="147b7-288">You can click the "…" button to browse to a path.</span></span>

4. <span data-ttu-id="147b7-289">Kliknutím na řádek **TypeName** se zobrazí znak "...". tlačítko.</span><span class="sxs-lookup"><span data-stu-id="147b7-289">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="147b7-290">Kliknutím na toto tlačítko otevřete **prohlížeč typu naslouchacího procesu trasování**, který můžete použít k vyhledání předem nakonfigurovaných posluchačů trasování, které jsou již nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="147b7-290">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>

5. <span data-ttu-id="147b7-291">Všimněte si **zdrojové** části.</span><span class="sxs-lookup"><span data-stu-id="147b7-291">Note the **Source** section.</span></span> <span data-ttu-id="147b7-292">Kliknutím na **Přidat** v této části otevřete dialogové okno s rozevírací nabídkou, která obsahuje seznam dostupných zdrojů trasování.</span><span class="sxs-lookup"><span data-stu-id="147b7-292">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="147b7-293">Vyberte zdroj trasování a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="147b7-293">Select a tracing source and click **OK**.</span></span>

6. <span data-ttu-id="147b7-294">Chcete-li upravit nastavení protokolování zpráv, klikněte na uzel **protokolování zpráv** .</span><span class="sxs-lookup"><span data-stu-id="147b7-294">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="147b7-295">Nastavení můžete upravit v mřížce vlastností.</span><span class="sxs-lookup"><span data-stu-id="147b7-295">You can edit the settings in the property grid.</span></span>

### <a name="advanced"></a><span data-ttu-id="147b7-296">Pokročilý</span><span class="sxs-lookup"><span data-stu-id="147b7-296">Advanced</span></span>

#### <a name="behaviors"></a><span data-ttu-id="147b7-297">Chování</span><span class="sxs-lookup"><span data-stu-id="147b7-297">Behaviors</span></span>

<span data-ttu-id="147b7-298">Uzel **chování** zobrazuje chování, která jsou aktuálně definována v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-298">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>

<span data-ttu-id="147b7-299">Konfigurace chování se používají ke konfiguraci chování koncových bodů a služeb.</span><span class="sxs-lookup"><span data-stu-id="147b7-299">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="147b7-300">Tato nastavení konfigurace se ukládají v uzlu **Upřesnit** v části **chování služby** a **chování koncového bodu**.</span><span class="sxs-lookup"><span data-stu-id="147b7-300">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="147b7-301">Služba používá chování služby; zatímco chování koncového bodu podle koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="147b7-301">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>

<span data-ttu-id="147b7-302">Chování jsou kolekce elementů rozšíření, které jsou pro zásobník.</span><span class="sxs-lookup"><span data-stu-id="147b7-302">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="147b7-303">Nejprve se použije element v horní části zásobníku.</span><span class="sxs-lookup"><span data-stu-id="147b7-303">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="147b7-304">Každý element rozšíření může mít svou vlastní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="147b7-304">Each extension element can have its own configuration.</span></span>

##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="147b7-305">Vytváří se nová konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="147b7-305">Creating a new Behavior Configuration</span></span>

<span data-ttu-id="147b7-306">Novou konfiguraci chování můžete vytvořit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="147b7-306">You can create a new behavior configuration in two ways.</span></span>

- <span data-ttu-id="147b7-307">Klikněte pravým tlačítkem na jeden z uzlů chování a vyberte možnost "**Nová konfigurace chování...**</span><span class="sxs-lookup"><span data-stu-id="147b7-307">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>

- <span data-ttu-id="147b7-308">Vyberte jeden z uzlů chování a klikněte na **konfiguraci nového chování**...</span><span class="sxs-lookup"><span data-stu-id="147b7-308">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="147b7-309">v **podokně úloh** v levém dolním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="147b7-309">in the **Task Pane** on the lower-left of the window.</span></span>

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="147b7-310">Přidání rozšíření prvků chování k chování</span><span class="sxs-lookup"><span data-stu-id="147b7-310">Adding Behavior Element Extensions to a Behavior</span></span>

1. <span data-ttu-id="147b7-311">Vyberte jeden z uzlů chování.</span><span class="sxs-lookup"><span data-stu-id="147b7-311">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="147b7-312">Vyberte chování, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="147b7-312">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="147b7-313">Klikněte na tlačítko **Add** (Přidat).</span><span class="sxs-lookup"><span data-stu-id="147b7-313">Click **Add**.</span></span>

4. <span data-ttu-id="147b7-314">V seznamu dostupných rozšíření vyberte rozšíření prvku chování, které chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="147b7-314">From the list of available extensions, select the behavior element extension you want to add.</span></span>

5. <span data-ttu-id="147b7-315">Klikněte na tlačítko **Add** (Přidat).</span><span class="sxs-lookup"><span data-stu-id="147b7-315">Click **Add**.</span></span>

##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="147b7-316">Úprava pozice rozšíření v chování</span><span class="sxs-lookup"><span data-stu-id="147b7-316">Adjusting the Extension Position in a Behavior</span></span>

<span data-ttu-id="147b7-317">Chování jsou kolekce prvků, které tvoří zásobník.</span><span class="sxs-lookup"><span data-stu-id="147b7-317">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="147b7-318">Každý prvek v zásobníku má svou vlastní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="147b7-318">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="147b7-319">Pořadí rozšíření prvků chování v chování určuje jejich pozice v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="147b7-319">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="147b7-320">Jako první se aplikují prvky v horní části zásobníku.</span><span class="sxs-lookup"><span data-stu-id="147b7-320">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="147b7-321">Postup změny řazení:</span><span class="sxs-lookup"><span data-stu-id="147b7-321">To change the ordering:</span></span>

1. <span data-ttu-id="147b7-322">Vyberte jeden z uzlů chování.</span><span class="sxs-lookup"><span data-stu-id="147b7-322">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="147b7-323">Vyberte chování, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="147b7-323">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="147b7-324">Vyberte prvek rozšíření chování v oddílu **pozice rozšíření chování elementu** .</span><span class="sxs-lookup"><span data-stu-id="147b7-324">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>

4. <span data-ttu-id="147b7-325">Chcete-li změnit pozici vybraného prvku, použijte tlačítko **nahoru** nebo **dolů** na levé straně seznamu.</span><span class="sxs-lookup"><span data-stu-id="147b7-325">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="147b7-326">Úprava konfigurace rozšíření prvků chování</span><span class="sxs-lookup"><span data-stu-id="147b7-326">Editing the Configuration of Behavior Element Extensions</span></span>

1. <span data-ttu-id="147b7-327">Vyberte jeden z uzlů chování ve stromu.</span><span class="sxs-lookup"><span data-stu-id="147b7-327">Select one of the behavior nodes in the tree.</span></span>

2. <span data-ttu-id="147b7-328">Vyberte chování, které obsahuje prvek, který chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="147b7-328">Select the behavior that contains the element you want to edit.</span></span>

3. <span data-ttu-id="147b7-329">Vyberte rozšíření prvku chování, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="147b7-329">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="147b7-330">Nastavení prvku se zobrazí v pravém podokně, kde je lze upravovat.</span><span class="sxs-lookup"><span data-stu-id="147b7-330">The settings of the element appear in the right pane where they can be edited.</span></span>

#### <a name="protocolmapping"></a><span data-ttu-id="147b7-331">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="147b7-331">ProtocolMapping</span></span>

<span data-ttu-id="147b7-332">V této části můžete nastavit výchozí typy vazeb pro různé protokoly, jako jsou http, TCP, MSMQ nebo NET. pipe, prostřednictvím definovaného mapování mezi schématy adres protokolů a možnými vazbami.</span><span class="sxs-lookup"><span data-stu-id="147b7-332">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="147b7-333">Můžete také přidat nová mapování na jiné protokoly.</span><span class="sxs-lookup"><span data-stu-id="147b7-333">You can also add new mappings to other protocols.</span></span>

#### <a name="extensions"></a><span data-ttu-id="147b7-334">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="147b7-334">Extensions</span></span>

<span data-ttu-id="147b7-335">Nová rozšíření vazby, rozšíření elementů vazby, standardní rozšíření koncových bodů a rozšíření chování lze zaregistrovat pro použití v konfiguraci služby WCF.</span><span class="sxs-lookup"><span data-stu-id="147b7-335">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="147b7-336">Rozšíření jsou páry název/typ.</span><span class="sxs-lookup"><span data-stu-id="147b7-336">Extensions are name/type pairs.</span></span> <span data-ttu-id="147b7-337">Název definuje název rozšíření v konfiguraci, zatímco typ implementuje rozšíření.</span><span class="sxs-lookup"><span data-stu-id="147b7-337">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="147b7-338">Existují čtyři typy rozšíření:</span><span class="sxs-lookup"><span data-stu-id="147b7-338">There are four types of extensions:</span></span>

- <span data-ttu-id="147b7-339">Rozšíření vazby definují celý typ vazby.</span><span class="sxs-lookup"><span data-stu-id="147b7-339">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="147b7-340">Příklad: `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="147b7-340">Example: `basicHttpBinding`.</span></span>

- <span data-ttu-id="147b7-341">Rozšíření elementu vazby definují prvek vazby.</span><span class="sxs-lookup"><span data-stu-id="147b7-341">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="147b7-342">Příklad: `textMessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="147b7-342">Example: `textMessageEncoding`.</span></span>

- <span data-ttu-id="147b7-343">Rozšíření Standard Endpoint Extensions definují celý standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="147b7-343">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="147b7-344">Příklad: `discoveryEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="147b7-344">Example: `discoveryEndpoint`.</span></span>

- <span data-ttu-id="147b7-345">Rozšíření prvků chování definují prvek chování.</span><span class="sxs-lookup"><span data-stu-id="147b7-345">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="147b7-346">Příklad: `clientVia`.</span><span class="sxs-lookup"><span data-stu-id="147b7-346">Example: `clientVia`.</span></span>

 <span data-ttu-id="147b7-347">Rozšíření, která byla registrována v konfiguraci, lze použít jako jakoukoli jinou komponentu WCF stejného typu.</span><span class="sxs-lookup"><span data-stu-id="147b7-347">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>

##### <a name="adding-a-new-extension"></a><span data-ttu-id="147b7-348">Přidání nového rozšíření</span><span class="sxs-lookup"><span data-stu-id="147b7-348">Adding a new extension</span></span>

<span data-ttu-id="147b7-349">Vyberte jeden z uzlů rozšíření v pokročilých uzlech:</span><span class="sxs-lookup"><span data-stu-id="147b7-349">Select one of the extension nodes in the advanced nodes:</span></span>

1. <span data-ttu-id="147b7-350">Klikněte na **Nový**.</span><span class="sxs-lookup"><span data-stu-id="147b7-350">Click **New**.</span></span>

2. <span data-ttu-id="147b7-351">Zadejte název a typ.</span><span class="sxs-lookup"><span data-stu-id="147b7-351">Enter a name and type.</span></span>

3. <span data-ttu-id="147b7-352">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="147b7-352">Click **OK**.</span></span>

4. <span data-ttu-id="147b7-353">Rozšíření se nyní zobrazí na příslušném místě v editoru.</span><span class="sxs-lookup"><span data-stu-id="147b7-353">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="147b7-354">Například pokud přidáte rozšíření prvku chování, zobrazí se v seznamu dostupných rozšíření.</span><span class="sxs-lookup"><span data-stu-id="147b7-354">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>

#### <a name="hosting-environment"></a><span data-ttu-id="147b7-355">Hostitelské prostředí</span><span class="sxs-lookup"><span data-stu-id="147b7-355">Hosting Environment</span></span>

<span data-ttu-id="147b7-356">Tato část umožňuje definovat nastavení vytváření instancí pro hostitelské prostředí služby.</span><span class="sxs-lookup"><span data-stu-id="147b7-356">This section allows you to define instantiation settings for the service hosting environment.</span></span>

### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="147b7-357">Vytvoření konfiguračního souboru pomocí Průvodce</span><span class="sxs-lookup"><span data-stu-id="147b7-357">Creating a Configuration File Using the Wizard</span></span>

<span data-ttu-id="147b7-358">Jedním ze způsobů, jak vytvořit nový konfigurační soubor, je použít Průvodce novým prvkem služby.</span><span class="sxs-lookup"><span data-stu-id="147b7-358">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="147b7-359">Průvodce najde nainstalované typy služeb a další prvky kompatibilní s WCF v počítači, včetně virtuálních adresářů služby COM+ a webhost, a načítají je, aby bylo možné konfiguraci mnohem zefektivnit.</span><span class="sxs-lookup"><span data-stu-id="147b7-359">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>

#### <a name="creating-a-configuration-file"></a><span data-ttu-id="147b7-360">Vytváření konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="147b7-360">Creating a Configuration File</span></span>

1. <span data-ttu-id="147b7-361">Spusťte editor konfigurace služby pomocí příkazového řádku a přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe` .</span><span class="sxs-lookup"><span data-stu-id="147b7-361">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="147b7-362">V nabídce **soubor** vyberte **otevřít** a klikněte na **spustitelný**soubor, **službu com+** nebo **službu webhosted Service**v závislosti na typu konfiguračního souboru, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="147b7-362">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>

3. <span data-ttu-id="147b7-363">V dialogovém okně **otevřít** přejděte do konkrétního souboru, pro který chcete vytvořit konfigurační soubor, a dvakrát na něj klikněte.</span><span class="sxs-lookup"><span data-stu-id="147b7-363">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>

4. <span data-ttu-id="147b7-364">V nabídce **soubor** přejděte na příkaz **Přidat novou položku** a klikněte na možnost **Služba**.</span><span class="sxs-lookup"><span data-stu-id="147b7-364">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="147b7-365">Otevře se Průvodce novým prvkem služby.</span><span class="sxs-lookup"><span data-stu-id="147b7-365">The New Service Element Wizard opens.</span></span>

5. <span data-ttu-id="147b7-366">Pomocí kroků v průvodci vytvořte novou službu.</span><span class="sxs-lookup"><span data-stu-id="147b7-366">Follow the steps in the wizard to create the new service.</span></span>

> [!NOTE]
> <span data-ttu-id="147b7-367">Chcete-li použít NetPeerTcpBinding z konfiguračního souboru vygenerovaného průvodcem, je nutné ručně přidat prvek konfigurace vazby a upravit `mode` atribut jeho `security` elementu na hodnotu None.</span><span class="sxs-lookup"><span data-stu-id="147b7-367">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>

## <a name="configuring-com"></a><span data-ttu-id="147b7-368">Konfigurace modelu COM+</span><span class="sxs-lookup"><span data-stu-id="147b7-368">Configuring COM+</span></span>

<span data-ttu-id="147b7-369">Editor konfigurace služby umožňuje vytvořit nový konfigurační soubor pro existující aplikaci modelu COM+ nebo upravit existující konfiguraci modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="147b7-369">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="147b7-370">Uzel **kontraktu com** je zobrazen pouze v případě, že `comContract` oddíl <> existuje v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-370">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>

### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="147b7-371">Vytváří se nová konfigurace COM+.</span><span class="sxs-lookup"><span data-stu-id="147b7-371">Creating a New COM+ Configuration</span></span>

<span data-ttu-id="147b7-372">Před vytvořením nové konfigurace COM+ se ujistěte, že je vaše aplikace COM+ nainstalovaná v rámci služby komponent a zaregistrovaná v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="147b7-372">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>

1. <span data-ttu-id="147b7-373">Výběr nabídky **soubor** – > **integraci**  ->  **aplikace modelu COM+.**</span><span class="sxs-lookup"><span data-stu-id="147b7-373">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="147b7-374">Tato operace zavře aktuální otevřený soubor.</span><span class="sxs-lookup"><span data-stu-id="147b7-374">This operation closes the current opened file.</span></span> <span data-ttu-id="147b7-375">Pokud se v aktuálním souboru nacházejí neuložená data, zobrazí se dialogové okno Uložit.</span><span class="sxs-lookup"><span data-stu-id="147b7-375">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="147b7-376">Pak se spustí **Průvodce integrací com+** .</span><span class="sxs-lookup"><span data-stu-id="147b7-376">The **COM+ Integration Wizard** is then launched.</span></span>

2. <span data-ttu-id="147b7-377">Na první stránce vyberte aplikaci COM+ ze stromu.</span><span class="sxs-lookup"><span data-stu-id="147b7-377">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="147b7-378">Pokud ve stromové struktuře nemůžete najít aplikaci modelu COM+, ověřte, zda je nainstalována do služby komponent a registrována v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="147b7-378">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>

3. <span data-ttu-id="147b7-379">Na další stránce vyberte, které metody chcete zveřejnit jako služby WCF.</span><span class="sxs-lookup"><span data-stu-id="147b7-379">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="147b7-380">Ve výchozím nastavení se zobrazí všechny podporované metody v aplikaci modelu COM+ a vybrané.</span><span class="sxs-lookup"><span data-stu-id="147b7-380">All the supported methods in the COM+ application are displayed and selected by default.</span></span>

4. <span data-ttu-id="147b7-381">Vyberte metodu hostování.</span><span class="sxs-lookup"><span data-stu-id="147b7-381">Choose a hosting method.</span></span>

5. <span data-ttu-id="147b7-382">Nakonfigurujte další nastavení podle průvodců v průvodci.</span><span class="sxs-lookup"><span data-stu-id="147b7-382">Configure other settings according to the guides in the wizard.</span></span>

6. <span data-ttu-id="147b7-383">Editor konfigurace služby používá ComSvcConfig.exe na pozadí ke generování konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="147b7-383">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="147b7-384">Po dokončení můžete zobrazit souhrn a ukončit průvodce.</span><span class="sxs-lookup"><span data-stu-id="147b7-384">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="147b7-385">Vygenerovaný konfigurační soubor je otevřen, aby jej bylo možné přímo upravit.</span><span class="sxs-lookup"><span data-stu-id="147b7-385">The generated configuration file is opened so that you can edit it directly.</span></span>

### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="147b7-386">Úprava existující konfigurace modelu COM+</span><span class="sxs-lookup"><span data-stu-id="147b7-386">Editing an Existing COM+ Configuration</span></span>

1. <span data-ttu-id="147b7-387">Vybrat nabídku **souborů** – > **otevřít**  ->  **službu com+**...</span><span class="sxs-lookup"><span data-stu-id="147b7-387">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>

2. <span data-ttu-id="147b7-388">V seznamu vyberte službu COM+, kterou chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="147b7-388">Select the COM+ Service you want to edit from the list.</span></span>

3. <span data-ttu-id="147b7-389">Upravte nastavení konfigurace v uzlu **kontrakty com** .</span><span class="sxs-lookup"><span data-stu-id="147b7-389">Edit configuration settings in the **COM Contracts** node.</span></span>

    > [!NOTE]
    > <span data-ttu-id="147b7-390">Můžete také přímo otevřít a upravit konfigurační soubor, který obsahuje smlouvy COM.</span><span class="sxs-lookup"><span data-stu-id="147b7-390">You can also directly open and edit a configuration file that contains COM contracts.</span></span>

## <a name="security"></a><span data-ttu-id="147b7-391">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="147b7-391">Security</span></span>

<span data-ttu-id="147b7-392">Není zaručeno zabezpečení konfiguračního souboru služby vygenerovaného editorem konfigurace.</span><span class="sxs-lookup"><span data-stu-id="147b7-392">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="147b7-393">Informace o tom, jak zabezpečit služby WCF, najdete v dokumentaci k [zabezpečení](./feature-details/security.md) .</span><span class="sxs-lookup"><span data-stu-id="147b7-393">Please refer to the [Security](./feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>

<span data-ttu-id="147b7-394">Kromě toho lze editor konfigurace použít pouze ke čtení a zápisu platných konfiguračních elementů WCF.</span><span class="sxs-lookup"><span data-stu-id="147b7-394">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="147b7-395">Nástroj ignoruje uživatelsky definované prvky, které odpovídají schématu.</span><span class="sxs-lookup"><span data-stu-id="147b7-395">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="147b7-396">Nepokouší se také odebrat tyto prvky z konfiguračního souboru nebo určit jejich účinky na známé elementy WCF.</span><span class="sxs-lookup"><span data-stu-id="147b7-396">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="147b7-397">Je zodpovědností uživatele určit, zda tyto prvky představují hrozbu pro aplikaci nebo systém.</span><span class="sxs-lookup"><span data-stu-id="147b7-397">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
