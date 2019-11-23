---
title: Nástroj Configuration Editor (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 3d482e2b03346c9443066c480575a1394324b9bf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320709"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="29279-102">Nástroj Configuration Editor (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="29279-102">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>

<span data-ttu-id="29279-103">Editor konfigurace služby Windows Communication Foundation (WCF) (SvcConfigEditor. exe) umožňuje správcům a vývojářům vytvářet a upravovat nastavení konfigurace služeb WCF pomocí grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29279-103">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="29279-104">Pomocí tohoto nástroje můžete spravovat nastavení vazeb WCF, chování, služeb a diagnostiky, aniž byste museli přímo upravovat konfigurační soubory XML.</span><span class="sxs-lookup"><span data-stu-id="29279-104">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>

<span data-ttu-id="29279-105">Editor konfigurace služby najdete ve složce C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span><span class="sxs-lookup"><span data-stu-id="29279-105">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>

## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="29279-106">Editor konfigurace WCF</span><span class="sxs-lookup"><span data-stu-id="29279-106">The WCF Configuration Editor</span></span>

<span data-ttu-id="29279-107">Editor konfigurace služby se dodává s průvodcem, který vás provede všemi kroky v části Konfigurace služby WCF nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="29279-107">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="29279-108">Důrazně doporučujeme použít Průvodce místo toho přímo v editoru.</span><span class="sxs-lookup"><span data-stu-id="29279-108">You are strongly advised to use the wizard instead of the editor directly.</span></span>

<span data-ttu-id="29279-109">Pokud už máte nějaké konfigurační soubory, které vyhovují standardnímu schématu System. Configuration, můžete spravovat konkrétní nastavení pro vazby, chování, služby a diagnostiku s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="29279-109">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="29279-110">Editor konfigurace služby umožňuje spravovat nastavení pro existující konfigurační soubory WCF i spustitelné soubory, služby modelu COM+ a služby hostované na webu.</span><span class="sxs-lookup"><span data-stu-id="29279-110">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="29279-111">Při otevírání služby hostované na webu pomocí editoru konfigurace služby se zobrazí jak vlastní konfigurace služby, tak zděděné konfigurace uzlů nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="29279-111">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>

<span data-ttu-id="29279-112">Vzhledem k tomu, že nastavení konfigurace WCF jsou umístěna v sekci `<system.serviceModel>` konfiguračního souboru, Editor pracuje výhradně s obsahem tohoto prvku a nepřistupuje k ostatním prvkům ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-112">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="29279-113">Můžete přímo přejít na existující konfigurační soubory nebo můžete vybrat sestavení, které obsahuje službu, virtuální adresář nebo službu COM+.</span><span class="sxs-lookup"><span data-stu-id="29279-113">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="29279-114">Editor načte konfigurační soubor pro danou službu a umožní uživateli buď přidat nové prvky, nebo upravit existující prvky vnořené v části `<system.serviceModel>` konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-114">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>

<span data-ttu-id="29279-115">Editor podporuje technologii IntelliSense a vynutil dodržování předpisů schématu.</span><span class="sxs-lookup"><span data-stu-id="29279-115">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="29279-116">Výsledný výstup je zaručený v dodržení schématu konfiguračního souboru a má syntakticky správné hodnoty dat.</span><span class="sxs-lookup"><span data-stu-id="29279-116">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="29279-117">Editor však nezaručuje, že konfigurační soubor je sémanticky platný.</span><span class="sxs-lookup"><span data-stu-id="29279-117">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="29279-118">Jinými slovy Editor nezaručuje, že konfigurační soubor může spolupracovat se službou, kterou konfiguruje.</span><span class="sxs-lookup"><span data-stu-id="29279-118">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>

> [!CAUTION]
> <span data-ttu-id="29279-119">Editor nemůže po úpravě elementu odstranit konfigurační prvek z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-119">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="29279-120">Pokud například použijete editor k nastavení názvu koncového bodu na neprázdný řetězec a uložíte ho, konfigurační soubor má následující obsah, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="29279-120">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> <span data-ttu-id="29279-121">Pokud se pokusíte odebrat název nastavením na prázdný řetězec a uložit soubor, konfigurační soubor stále obsahuje atribut `name`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="29279-121">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> <span data-ttu-id="29279-122">Chcete-li tento atribut vyprázdnit, je nutné ručně upravit element pomocí jiného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="29279-122">To purge the attribute, you must manually edit the element using another text editor.</span></span>
>
> <span data-ttu-id="29279-123">Při použití `issueToken`ho prvku `clientCredential`ho koncového bodu byste měli být obzvláště opatrní u tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="29279-123">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="29279-124">Konkrétně atribut `address` jeho dílčího prvku `localIssuer` nesmí být prázdným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="29279-124">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="29279-125">Pokud jste změnili atribut `address` pomocí editoru konfigurace a chcete ho úplně odebrat, měli byste použít jiný nástroj než Editor.</span><span class="sxs-lookup"><span data-stu-id="29279-125">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="29279-126">V opačném případě atribut obsahuje prázdný řetězec a vaše aplikace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="29279-126">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>

## <a name="using-the-configuration-editor"></a><span data-ttu-id="29279-127">Použití editoru konfigurace</span><span class="sxs-lookup"><span data-stu-id="29279-127">Using the Configuration Editor</span></span>

<span data-ttu-id="29279-128">Editor konfigurací služby najdete v následujících Windows SDK umístění instalace:</span><span class="sxs-lookup"><span data-stu-id="29279-128">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>

<span data-ttu-id="29279-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="29279-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>

<span data-ttu-id="29279-130">Po spuštění editoru konfigurace služby můžete pomocí nabídky **soubor/otevřít** vyhledat službu nebo sestavení, které chcete spravovat.</span><span class="sxs-lookup"><span data-stu-id="29279-130">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="29279-131">Můžete otevřít konfigurační soubory přímo, vyhledat WCF/COM + Services a otevřít konfigurační soubory pro služby hostované na webu.</span><span class="sxs-lookup"><span data-stu-id="29279-131">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>

<span data-ttu-id="29279-132">Uživatelské rozhraní editoru konfigurace služby je rozdělené do následujících oblastí:</span><span class="sxs-lookup"><span data-stu-id="29279-132">The Service Configuration Editor's user interface is divided into the following areas:</span></span>

- <span data-ttu-id="29279-133">Podokno stromového zobrazení, které zobrazuje prvky konfigurace ve stromové struktuře vlevo.</span><span class="sxs-lookup"><span data-stu-id="29279-133">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="29279-134">Kliknutím pravým tlačítkem myši na uzly můžete provádět operace ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="29279-134">You can perform operations in the tree by right-clicking the nodes.</span></span>

- <span data-ttu-id="29279-135">Podokno úloh, které zobrazuje běžné úkoly pro aktuální prvky v levém dolním rohu okna</span><span class="sxs-lookup"><span data-stu-id="29279-135">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>

- <span data-ttu-id="29279-136">Podokno podrobností, které zobrazuje podrobné nastavení uzlu Konfigurace vybraného ve stromovém zobrazení vpravo.</span><span class="sxs-lookup"><span data-stu-id="29279-136">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>

### <a name="opening-a-configuration-file"></a><span data-ttu-id="29279-137">Otevření konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="29279-137">Opening a Configuration File</span></span>

1. <span data-ttu-id="29279-138">Spusťte editor konfigurace služby pomocí příkazového řádku a přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe`.</span><span class="sxs-lookup"><span data-stu-id="29279-138">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="29279-139">V nabídce **soubor** vyberte **otevřít** a klikněte na typ souboru, který chcete spravovat.</span><span class="sxs-lookup"><span data-stu-id="29279-139">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>

3. <span data-ttu-id="29279-140">V dialogovém okně **otevřít** přejděte na konkrétní soubor, který chcete spravovat, a dvakrát na něj klikněte.</span><span class="sxs-lookup"><span data-stu-id="29279-140">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>

<span data-ttu-id="29279-141">Prohlížeč automaticky sleduje cestu sloučení konfigurace a vytvoří zobrazení sloučené konfigurace.</span><span class="sxs-lookup"><span data-stu-id="29279-141">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="29279-142">Například skutečná konfigurace nehostované služby je kombinací souboru Machine. config a App. config. Všechny změny se aplikují na aktivní soubor v SvcConfigEditor.</span><span class="sxs-lookup"><span data-stu-id="29279-142">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="29279-143">Pokud chcete upravit konkrétní soubor v cestě pro sloučení konfigurace, měli byste ho otevřít přímo.</span><span class="sxs-lookup"><span data-stu-id="29279-143">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>

> [!NOTE]
> <span data-ttu-id="29279-144">Editor konfigurací znovu načte aktuálně otevřený konfigurační soubor, když byl druhý upravený mimo editor.</span><span class="sxs-lookup"><span data-stu-id="29279-144">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="29279-145">Pokud k tomu dojde, všechny změny, které nejsou uložené v editoru trvale, se ztratí.</span><span class="sxs-lookup"><span data-stu-id="29279-145">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="29279-146">Pokud probíhá opětovné načítání konzistentně, nejpravděpodobnější příčinou je služba, která nepřetržitě přistupuje ke konfiguračnímu souboru, například antivirový software spuštěný na pozadí.</span><span class="sxs-lookup"><span data-stu-id="29279-146">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="29279-147">Chcete-li tento problém vyřešit, zajistěte, aby byl Editor konfigurací jediným procesem, který má přístup k souboru při jeho otevření.</span><span class="sxs-lookup"><span data-stu-id="29279-147">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>

### <a name="services"></a><span data-ttu-id="29279-148">Služby</span><span class="sxs-lookup"><span data-stu-id="29279-148">Services</span></span>

<span data-ttu-id="29279-149">Uzel **služby** zobrazí všechny služby, které jsou aktuálně přiřazeny k konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-149">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="29279-150">Každý dílčí uzel ve stromové struktuře odpovídá dílčímu elementu <`services`> elementu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-150">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>

<span data-ttu-id="29279-151">Když kliknete na uzel **služby** , můžete zobrazit nebo provádět úlohy na stránce Souhrn služby v podokně **podrobností** .</span><span class="sxs-lookup"><span data-stu-id="29279-151">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>

#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="29279-152">Vytváří se nová konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="29279-152">Creating a new Service Configuration</span></span>

<span data-ttu-id="29279-153">Novou konfiguraci služby můžete vytvořit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="29279-153">You can create a new service configuration in the following ways:</span></span>

- <span data-ttu-id="29279-154">Pomocí Průvodce: klikněte na odkaz **vytvořit novou službu...**</span><span class="sxs-lookup"><span data-stu-id="29279-154">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="29279-155">na stránce podokno úloh nebo souhrn spusťte průvodce.</span><span class="sxs-lookup"><span data-stu-id="29279-155">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="29279-156">Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="29279-156">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="29279-157">Ruční vytvoření: můžete kliknout pravým tlačítkem myši na uzel **služby** a vybrat možnost **Nová služba**.</span><span class="sxs-lookup"><span data-stu-id="29279-157">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>

#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="29279-158">Vytváří se nová konfigurace koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="29279-158">Creating a new Service Endpoint Configuration</span></span>

<span data-ttu-id="29279-159">Novou konfiguraci koncového bodu služby můžete vytvořit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="29279-159">You can create a new service endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="29279-160">Vytvořit pomocí Průvodce: klikněte na odkaz **vytvořit nový koncový bod služby...**</span><span class="sxs-lookup"><span data-stu-id="29279-160">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="29279-161">na stránce podokno úloh nebo souhrn spusťte průvodce.</span><span class="sxs-lookup"><span data-stu-id="29279-161">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="29279-162">Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="29279-162">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="29279-163">Vytvořit ručně: po vytvoření služby můžete kliknout pravým tlačítkem myši na uzel **koncové body** a zvolit**Nový koncový bod služby**.</span><span class="sxs-lookup"><span data-stu-id="29279-163">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>

#### <a name="editing-a-service-configuration"></a><span data-ttu-id="29279-164">Úprava konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="29279-164">Editing a Service Configuration</span></span>

1. <span data-ttu-id="29279-165">Klikněte na uzel **služby** .</span><span class="sxs-lookup"><span data-stu-id="29279-165">Click a **Service** node.</span></span>

2. <span data-ttu-id="29279-166">Upravte nastavení v Gridech vlastností.</span><span class="sxs-lookup"><span data-stu-id="29279-166">Edit the settings in the property grids.</span></span>

#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="29279-167">Úprava konfigurace koncového bodu služby</span><span class="sxs-lookup"><span data-stu-id="29279-167">Editing a Service Endpoint Configuration</span></span>

1. <span data-ttu-id="29279-168">Klikněte na uzel **koncového bodu služby** .</span><span class="sxs-lookup"><span data-stu-id="29279-168">Click a **Service Endpoint** node.</span></span>

2. <span data-ttu-id="29279-169">Upravte nastavení v Gridech vlastností.</span><span class="sxs-lookup"><span data-stu-id="29279-169">Edit the settings in the property grids.</span></span>

#### <a name="adding-a-base-address"></a><span data-ttu-id="29279-170">Přidání základní adresy</span><span class="sxs-lookup"><span data-stu-id="29279-170">Adding a Base Address</span></span>

1. <span data-ttu-id="29279-171">Klikněte na uzel **hostitele** .</span><span class="sxs-lookup"><span data-stu-id="29279-171">Click the **Host** node.</span></span>

2. <span data-ttu-id="29279-172">Klikněte na **Nový...**</span><span class="sxs-lookup"><span data-stu-id="29279-172">Click the **New…**</span></span> <span data-ttu-id="29279-173">tlačítko v části **základní adresy** .</span><span class="sxs-lookup"><span data-stu-id="29279-173">button in the **Base Addresses** section.</span></span>

3. <span data-ttu-id="29279-174">Do dialogového okna zadejte identifikátor URI základní adresy.</span><span class="sxs-lookup"><span data-stu-id="29279-174">Type in the base address URI in the dialog box.</span></span>

4. <span data-ttu-id="29279-175">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="29279-175">Click **OK**.</span></span>

> [!NOTE]
> <span data-ttu-id="29279-176">V tomto nástroji nelze upravit hodnotu [\<baseAddressPrefixFilters >](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) .</span><span class="sxs-lookup"><span data-stu-id="29279-176">You cannot edit the value of [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="29279-177">Chcete-li přidat nebo upravit tento prvek, měli byste použít textový editor nebo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29279-177">To add or modify this element, you should use a text editor or Visual Studio.</span></span>

### <a name="client"></a><span data-ttu-id="29279-178">Klient</span><span class="sxs-lookup"><span data-stu-id="29279-178">Client</span></span>

<span data-ttu-id="29279-179">Uzel **klienta** zobrazí všechny koncové body klienta v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-179">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="29279-180">Každý dílčí uzel ve stromové struktuře odpovídá dílčímu elementu <`client`> elementu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-180">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>

<span data-ttu-id="29279-181">Po kliknutí na uzel **klienta** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** klienta v **podokně podrobností**.</span><span class="sxs-lookup"><span data-stu-id="29279-181">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="29279-182">Vytváří se nová konfigurace koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="29279-182">Creating a new Client Endpoint Configuration</span></span>

<span data-ttu-id="29279-183">Novou konfiguraci koncového bodu klienta můžete vytvořit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="29279-183">You can create a new client endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="29279-184">Průvodce vytvořením: kliknutím na odkaz **vytvořit nového klienta...**</span><span class="sxs-lookup"><span data-stu-id="29279-184">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="29279-185">v **podokně úloh** v levém dolním rohu okna nebo **souhrnu** spusťte průvodce.</span><span class="sxs-lookup"><span data-stu-id="29279-185">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="29279-186">Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="29279-186">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="29279-187">Průvodce vás vyzve, abyste odkazovali na umístění konfigurace služby, ze které se vygenerovala konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="29279-187">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="29279-188">Pak můžete zvolit koncový bod služby, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="29279-188">You can then choose the service endpoint to connect to.</span></span>

- <span data-ttu-id="29279-189">Ruční vytvoření: klikněte pravým tlačítkem na uzel **koncové body** v části **klient**a vyberte **Nový koncový bod klienta**.</span><span class="sxs-lookup"><span data-stu-id="29279-189">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>

#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="29279-190">Úprava konfigurace koncového bodu klienta</span><span class="sxs-lookup"><span data-stu-id="29279-190">Editing a Client Endpoint Configuration</span></span>

1. <span data-ttu-id="29279-191">Klikněte na uzel **koncového bodu klienta** .</span><span class="sxs-lookup"><span data-stu-id="29279-191">Click a **Client Endpoint** node.</span></span>

2. <span data-ttu-id="29279-192">Upravte nastavení v Gridech vlastností.</span><span class="sxs-lookup"><span data-stu-id="29279-192">Edit the settings in the property grids.</span></span>

### <a name="standard-endpoint"></a><span data-ttu-id="29279-193">Standardní koncový bod</span><span class="sxs-lookup"><span data-stu-id="29279-193">Standard Endpoint</span></span>

<span data-ttu-id="29279-194">Standardní koncové body jsou specializované koncové body, které mají jednu nebo více aspektů adresy, kontraktu a vazby nastavené na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29279-194">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>

<span data-ttu-id="29279-195">Taková nastavení konfigurace se ukládají do uzlu **standardního koncového bodu** .</span><span class="sxs-lookup"><span data-stu-id="29279-195">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="29279-196">Uzel **standardního koncového bodu** zobrazí všechna nastavení standardního koncového bodu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-196">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="29279-197">Každý dílčí uzel ve stromové struktuře odpovídá dílčímu prvku v elementu `<standardEndpoints>` v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-197">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>

<span data-ttu-id="29279-198">Když kliknete na uzel **standardního koncového bodu** , můžete zobrazit nebo provádět úlohy na **stránce Souhrn** standardního koncového bodu v **podokně podrobností**.</span><span class="sxs-lookup"><span data-stu-id="29279-198">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="29279-199">Vytváří se nová konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="29279-199">Creating a New Standard Endpoint Configuration</span></span>

<span data-ttu-id="29279-200">Novou konfiguraci standardního koncového bodu můžete vytvořit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="29279-200">You can create a new standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="29279-201">Klikněte pravým tlačítkem na uzel **standardní koncový bod** a vyberte **Nová konfigurace standardního koncového bodu...**</span><span class="sxs-lookup"><span data-stu-id="29279-201">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="29279-202">V dialogovém okně vyberte typ vazby a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="29279-202">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="29279-203">Vyberte uzel **standardního koncového bodu** a klikněte na **nový standardní konfigurace koncového bodu...**</span><span class="sxs-lookup"><span data-stu-id="29279-203">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="29279-204">v **podokně úloh** v levém dolním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="29279-204">in the **Task Pane** on the lower-left of the window.</span></span>

<span data-ttu-id="29279-205">Zobrazí se dialogové okno **Vytvoření nového standardního koncového bodu** , ve kterém jsou uvedeny všechny registrované standardní typy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="29279-205">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="29279-206">Zobrazení a úprava konfigurace standardního koncového bodu</span><span class="sxs-lookup"><span data-stu-id="29279-206">Viewing and Editing a Standard Endpoint Configuration</span></span>

<span data-ttu-id="29279-207">Konfiguraci standardního koncového bodu můžete otevřít pro zobrazení a úpravy následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="29279-207">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>

- <span data-ttu-id="29279-208">Kliknutím rozbalte uzel **standardní koncový bod** a klikněte na příslušný dílčí uzel koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="29279-208">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>

- <span data-ttu-id="29279-209">Klikněte na uzel **standardní koncový bod** a v podokně podrobností klikněte na příslušný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="29279-209">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>

<span data-ttu-id="29279-210">Atributy koncového bodu jsou zobrazeny v pravém podokně pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="29279-210">Attributes for the endpoint are shown in the right pane for editing.</span></span>

#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="29279-211">Odstraňuje se konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="29279-211">Deleting a Standard Endpoint Configuration</span></span>

<span data-ttu-id="29279-212">Konfiguraci standardních koncových bodů můžete odstranit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="29279-212">You can delete a standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="29279-213">Kliknutím rozbalte uzel **standardní koncový bod** a klikněte pravým tlačítkem myši na příslušný dílčí uzel koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="29279-213">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="29279-214">K odstranění koncového bodu použijte kontextový příkaz **Odstranit konfiguraci standardního koncového bodu** .</span><span class="sxs-lookup"><span data-stu-id="29279-214">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>

- <span data-ttu-id="29279-215">Klikněte na uzel **standardní koncový bod** .</span><span class="sxs-lookup"><span data-stu-id="29279-215">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="29279-216">V podokně **úloh** klikněte na **Odstranit standardní konfiguraci koncového bodu**.</span><span class="sxs-lookup"><span data-stu-id="29279-216">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>

<span data-ttu-id="29279-217">Pokud se používá standardní koncový bod, při pokusu o odstranění se zobrazí varovná zpráva: **standardní koncový bod se používá. Pokud ho odstraníte nyní, nezapomeňte odstranit všechny jeho odkazy v jiných částech konfigurace (například v koncovém bodu služby nebo koncovém bodu klienta). V opačném případě bude konfigurace neplatná a nedá se otevřít příště. Opravdu chcete odstranit standardní koncový bod? "**</span><span class="sxs-lookup"><span data-stu-id="29279-217">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>

### <a name="binding"></a><span data-ttu-id="29279-218">Vazba</span><span class="sxs-lookup"><span data-stu-id="29279-218">Binding</span></span>

<span data-ttu-id="29279-219">Konfigurace vazeb se používají ke konfiguraci vazeb u koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="29279-219">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="29279-220">Taková nastavení konfigurace jsou uložena v uzlu **vazby** .</span><span class="sxs-lookup"><span data-stu-id="29279-220">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="29279-221">Konfigurace odkazu na koncové body podle názvu a více koncových bodů může odkazovat na konfiguraci jedné vazby.</span><span class="sxs-lookup"><span data-stu-id="29279-221">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>

<span data-ttu-id="29279-222">Uzel **vazby** zobrazí všechna nastavení vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-222">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="29279-223">Každý dílčí uzel ve stromové struktuře odpovídá dílčímu prvku v <`bindings`> elementu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-223">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>

<span data-ttu-id="29279-224">Po kliknutí na uzel **vazby** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** vazby v **podokně podrobností**.</span><span class="sxs-lookup"><span data-stu-id="29279-224">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="29279-225">Vytváří se nová konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="29279-225">Creating a New Binding Configuration</span></span>

<span data-ttu-id="29279-226">Novou konfiguraci vazby můžete vytvořit následujícími způsoby.</span><span class="sxs-lookup"><span data-stu-id="29279-226">You can create a new binding configuration in the following ways.</span></span>

- <span data-ttu-id="29279-227">Klikněte pravým tlačítkem myši na uzel **vazby** a vyberte možnost **Nová konfigurace vazby**...</span><span class="sxs-lookup"><span data-stu-id="29279-227">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="29279-228">V dialogovém okně vyberte typ vazby a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="29279-228">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="29279-229">Vyberte uzel **vazby** a klikněte na **Nová konfigurace vazby**...</span><span class="sxs-lookup"><span data-stu-id="29279-229">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="29279-230">v **podokně úloh** v levém dolním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="29279-230">in the **Task Pane** on the lower-left of the window.</span></span>

- <span data-ttu-id="29279-231">Na stránce Souhrn služby nebo klienta klikněte na **kliknutím na tlačítko vytvořit** v poli **Konfigurace vazby** vytvořte konfiguraci vazby pro odpovídající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="29279-231">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="29279-232">Přidání rozšíření elementu vazby k vlastní vazbě</span><span class="sxs-lookup"><span data-stu-id="29279-232">Adding Binding Element Extensions to a Custom Binding</span></span>

1. <span data-ttu-id="29279-233">Vyberte vazbu, do které chcete přidat prvek rozšíření.</span><span class="sxs-lookup"><span data-stu-id="29279-233">Select the binding you want to add an extension element to.</span></span>

2. <span data-ttu-id="29279-234">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="29279-234">Click **Add**.</span></span>

3. <span data-ttu-id="29279-235">V seznamu dostupných rozšíření vyberte rozšíření prvku vazby, které chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="29279-235">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="29279-236">Chcete-li vybrat více položek, stiskněte současně klávesu CTRL.</span><span class="sxs-lookup"><span data-stu-id="29279-236">To select multiple items, press the CTRL key simultaneously.</span></span>

4. <span data-ttu-id="29279-237">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="29279-237">Click **Add**.</span></span>

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="29279-238">Úprava pozice rozšíření ve vlastní vazbě</span><span class="sxs-lookup"><span data-stu-id="29279-238">Adjusting the Extension Position in a Custom Binding</span></span>

<span data-ttu-id="29279-239">Vlastní vazba je kolekce elementů vazby, které tvoří zásobník.</span><span class="sxs-lookup"><span data-stu-id="29279-239">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="29279-240">Každý prvek vazby v zásobníku má vlastní nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="29279-240">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="29279-241">Pořadí rozšíření prvků vazby ve vlastní vazbě označuje jejich pozice v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="29279-241">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="29279-242">Jako první se aplikují prvky v horní části zásobníku.</span><span class="sxs-lookup"><span data-stu-id="29279-242">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="29279-243">Postup změny řazení:</span><span class="sxs-lookup"><span data-stu-id="29279-243">To change the ordering:</span></span>

1. <span data-ttu-id="29279-244">Vyberte vlastní uzel vazby.</span><span class="sxs-lookup"><span data-stu-id="29279-244">Select the custom binding node.</span></span>

2. <span data-ttu-id="29279-245">Vyberte jeden prvek rozšíření vazby v oddílu **pozice rozšíření vazby elementu** .</span><span class="sxs-lookup"><span data-stu-id="29279-245">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>

3. <span data-ttu-id="29279-246">Chcete-li změnit pozici vybraného prvku, použijte tlačítko **nahoru** nebo **dolů** na levé straně seznamu.</span><span class="sxs-lookup"><span data-stu-id="29279-246">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="29279-247">Úprava konfigurace rozšíření elementu vazby ve vlastní vazbě</span><span class="sxs-lookup"><span data-stu-id="29279-247">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>

1. <span data-ttu-id="29279-248">Vyberte uzel vazby ve stromu.</span><span class="sxs-lookup"><span data-stu-id="29279-248">Select the binding node in the tree.</span></span>

2. <span data-ttu-id="29279-249">Vyberte vlastní vazbu obsahující prvek, který chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="29279-249">Select the custom binding that contains the element you want to edit.</span></span>

3. <span data-ttu-id="29279-250">Vyberte rozšíření prvku vazby, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="29279-250">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="29279-251">Nastavení prvku se zobrazí v pravém podokně, kde je lze upravovat.</span><span class="sxs-lookup"><span data-stu-id="29279-251">The settings of the element appear in the right pane, where they can be edited.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="29279-252">Diagnostika</span><span class="sxs-lookup"><span data-stu-id="29279-252">Diagnostics</span></span>

<span data-ttu-id="29279-253">V uzlu **Diagnostika** se zobrazí všechna nastavení diagnostiky v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-253">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="29279-254">Umožňuje zapnout nebo vypnout čítače výkonu, povolit nebo zakázat rozhraní WMI (Windows Management Instrumentation) (WMI), nakonfigurovat trasování WCF a nakonfigurovat protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="29279-254">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="29279-255">Nastavení v uzlu **Diagnostika** odpovídá části <`system.diagnostics`> a `<diagnostics>` oddílu v `<system.serviceModel>` konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-255">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>

<span data-ttu-id="29279-256">Po kliknutí na uzel **Diagnostika** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** diagnostiky v **podokně podrobností**.</span><span class="sxs-lookup"><span data-stu-id="29279-256">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="29279-257">Konfigurace čítačů výkonu a rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="29279-257">Configuring performance counters and WMI</span></span>

1. <span data-ttu-id="29279-258">Klikněte na uzel **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="29279-258">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="29279-259">Klikněte na **Přepnout čítače výkonu**.</span><span class="sxs-lookup"><span data-stu-id="29279-259">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="29279-260">Čítač výkonu má tři stavy: vypnuto (výchozí), ServiceOnly a All.</span><span class="sxs-lookup"><span data-stu-id="29279-260">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="29279-261">Kliknutím na odkaz přepnete nastavení mezi těmito třemi stavy.</span><span class="sxs-lookup"><span data-stu-id="29279-261">Clicking the link toggles the setting among these three states.</span></span>

#### <a name="configuring-wmi-provider"></a><span data-ttu-id="29279-262">Konfigurace zprostředkovatele rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="29279-262">Configuring WMI Provider</span></span>

1. <span data-ttu-id="29279-263">Klikněte na uzel **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="29279-263">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="29279-264">Pokud chcete povolit zprostředkovatele rozhraní WMI, klikněte na odkaz **Povolit zprostředkovatele rozhraní WMI** .</span><span class="sxs-lookup"><span data-stu-id="29279-264">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>

#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="29279-265">Povolení trasování WCF</span><span class="sxs-lookup"><span data-stu-id="29279-265">Enabling WCF Tracing</span></span>

<span data-ttu-id="29279-266">Můžete vytvořit trasovací soubor WCF se standardními vlastnostmi nebo nastavit vlastní trasovací soubor.</span><span class="sxs-lookup"><span data-stu-id="29279-266">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="29279-267">Klikněte na uzel **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="29279-267">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="29279-268">Klikněte na **Povolit trasování**.</span><span class="sxs-lookup"><span data-stu-id="29279-268">Click **Enable Tracing**.</span></span>

3. <span data-ttu-id="29279-269">Kliknutím na odkaz **úroveň trasování** upravíte úroveň trasování.</span><span class="sxs-lookup"><span data-stu-id="29279-269">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="29279-270">Existuje šest úrovní trasování: vypnuto, kritická, chyba, upozornění, informace a podrobné.</span><span class="sxs-lookup"><span data-stu-id="29279-270">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="29279-271">Možnost **trasování aktivity** a **šíření** aktivity umožňuje použít funkci trasování aktivity WCF.</span><span class="sxs-lookup"><span data-stu-id="29279-271">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>

4. <span data-ttu-id="29279-272">Klikněte na název naslouchacího procesu trasování a určete trasovací soubor a možnosti.</span><span class="sxs-lookup"><span data-stu-id="29279-272">Click the trace listener name to specify the trace file and options.</span></span>

#### <a name="enabling-wcf-logging"></a><span data-ttu-id="29279-273">Povolení protokolování WCF</span><span class="sxs-lookup"><span data-stu-id="29279-273">Enabling WCF Logging</span></span>

<span data-ttu-id="29279-274">Můžete vytvořit trasovací soubor WCF se standardními vlastnostmi nebo nastavit vlastní trasovací soubor.</span><span class="sxs-lookup"><span data-stu-id="29279-274">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="29279-275">Klikněte na uzel **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="29279-275">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="29279-276">Klikněte na **Povolit protokolování zpráv**.</span><span class="sxs-lookup"><span data-stu-id="29279-276">Click **Enable Message Logging**.</span></span>

3. <span data-ttu-id="29279-277">Kliknutím na odkaz **úroveň protokolu** upravíte úroveň protokolu.</span><span class="sxs-lookup"><span data-stu-id="29279-277">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="29279-278">Existují tři úrovně protokolu: chybné, služba a přenos.</span><span class="sxs-lookup"><span data-stu-id="29279-278">There are three log levels: Malformed, Service, and Transport.</span></span>

4. <span data-ttu-id="29279-279">Klikněte na název naslouchacího procesu a určete soubor protokolu a možnosti.</span><span class="sxs-lookup"><span data-stu-id="29279-279">Click the listener name to specify the log file and options.</span></span>

> [!NOTE]
> <span data-ttu-id="29279-280">Pokud chcete, aby se protokoly trasování a zpráv vyprázdny automaticky, když je vaše aplikace zavřená, povolte možnost **automatického vyprázdnit** .</span><span class="sxs-lookup"><span data-stu-id="29279-280">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>

<span data-ttu-id="29279-281">**Stránka Souhrn** **diagnostiky** umožňuje provádět nejběžnější úlohy v konfiguraci diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="29279-281">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="29279-282">Pokud však chcete ručně upravit nastavení naslouchacího procesu a zdrojů, je nutné rozbalit uzel **Diagnostika** a upravit nastavení v uzlu **protokolování zpráv**, **naslouchací procesy** a **zdroje** .</span><span class="sxs-lookup"><span data-stu-id="29279-282">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="29279-283">Povolení vlastního trasování WCF nebo protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="29279-283">Enabling WCF Custom Tracing or Message Logging</span></span>

1. <span data-ttu-id="29279-284">Klikněte na uzel **Diagnostika** a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="29279-284">Click the **Diagnostics** node, and expand it.</span></span>

2. <span data-ttu-id="29279-285">Klikněte pravým tlačítkem myši na uzel **naslouchací procesy** a vyberte možnost **nový naslouchací proces**.</span><span class="sxs-lookup"><span data-stu-id="29279-285">Right-click the **Listeners** node and select **New Listener**.</span></span>

3. <span data-ttu-id="29279-286">Do pole **InitData** zadejte název trasovacího souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-286">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="29279-287">Můžete kliknout na tlačítko "..." tlačítko pro procházení k cestě.</span><span class="sxs-lookup"><span data-stu-id="29279-287">You can click the "…" button to browse to a path.</span></span>

4. <span data-ttu-id="29279-288">Kliknutím na řádek **TypeName** se zobrazí znak "...". tlačítko.</span><span class="sxs-lookup"><span data-stu-id="29279-288">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="29279-289">Kliknutím na toto tlačítko otevřete **prohlížeč typu naslouchacího procesu trasování**, který můžete použít k vyhledání předem nakonfigurovaných posluchačů trasování, které jsou již nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="29279-289">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>

5. <span data-ttu-id="29279-290">Všimněte si **zdrojové** části.</span><span class="sxs-lookup"><span data-stu-id="29279-290">Note the **Source** section.</span></span> <span data-ttu-id="29279-291">Kliknutím na **Přidat** v této části otevřete dialogové okno s rozevírací nabídkou, která obsahuje seznam dostupných zdrojů trasování.</span><span class="sxs-lookup"><span data-stu-id="29279-291">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="29279-292">Vyberte zdroj trasování a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="29279-292">Select a tracing source and click **OK**.</span></span>

6. <span data-ttu-id="29279-293">Chcete-li upravit nastavení protokolování zpráv, klikněte na uzel **protokolování zpráv** .</span><span class="sxs-lookup"><span data-stu-id="29279-293">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="29279-294">Nastavení můžete upravit v mřížce vlastností.</span><span class="sxs-lookup"><span data-stu-id="29279-294">You can edit the settings in the property grid.</span></span>

### <a name="advanced"></a><span data-ttu-id="29279-295">Upřesnit</span><span class="sxs-lookup"><span data-stu-id="29279-295">Advanced</span></span>

#### <a name="behaviors"></a><span data-ttu-id="29279-296">Chování</span><span class="sxs-lookup"><span data-stu-id="29279-296">Behaviors</span></span>

<span data-ttu-id="29279-297">Uzel **chování** zobrazuje chování, která jsou aktuálně definována v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-297">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>

<span data-ttu-id="29279-298">Konfigurace chování se používají ke konfiguraci chování koncových bodů a služeb.</span><span class="sxs-lookup"><span data-stu-id="29279-298">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="29279-299">Tato nastavení konfigurace se ukládají v uzlu **Upřesnit** v části **chování služby** a **chování koncového bodu**.</span><span class="sxs-lookup"><span data-stu-id="29279-299">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="29279-300">Služba používá chování služby; zatímco chování koncového bodu podle koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="29279-300">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>

<span data-ttu-id="29279-301">Chování jsou kolekce elementů rozšíření, které jsou pro zásobník.</span><span class="sxs-lookup"><span data-stu-id="29279-301">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="29279-302">Nejprve se použije element v horní části zásobníku.</span><span class="sxs-lookup"><span data-stu-id="29279-302">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="29279-303">Každý element rozšíření může mít svou vlastní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="29279-303">Each extension element can have its own configuration.</span></span>

##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="29279-304">Vytváří se nová konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="29279-304">Creating a new Behavior Configuration</span></span>

<span data-ttu-id="29279-305">Novou konfiguraci chování můžete vytvořit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="29279-305">You can create a new behavior configuration in two ways.</span></span>

- <span data-ttu-id="29279-306">Klikněte pravým tlačítkem na jeden z uzlů chování a vyberte možnost "**Nová konfigurace chování...**</span><span class="sxs-lookup"><span data-stu-id="29279-306">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>

- <span data-ttu-id="29279-307">Vyberte jeden z uzlů chování a klikněte na **konfiguraci nového chování**...</span><span class="sxs-lookup"><span data-stu-id="29279-307">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="29279-308">v **podokně úloh** v levém dolním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="29279-308">in the **Task Pane** on the lower-left of the window.</span></span>

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="29279-309">Přidání rozšíření prvků chování k chování</span><span class="sxs-lookup"><span data-stu-id="29279-309">Adding Behavior Element Extensions to a Behavior</span></span>

1. <span data-ttu-id="29279-310">Vyberte jeden z uzlů chování.</span><span class="sxs-lookup"><span data-stu-id="29279-310">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="29279-311">Vyberte chování, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="29279-311">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="29279-312">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="29279-312">Click **Add**.</span></span>

4. <span data-ttu-id="29279-313">V seznamu dostupných rozšíření vyberte rozšíření prvku chování, které chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="29279-313">From the list of available extensions, select the behavior element extension you want to add.</span></span>

5. <span data-ttu-id="29279-314">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="29279-314">Click **Add**.</span></span>

##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="29279-315">Úprava pozice rozšíření v chování</span><span class="sxs-lookup"><span data-stu-id="29279-315">Adjusting the Extension Position in a Behavior</span></span>

<span data-ttu-id="29279-316">Chování jsou kolekce prvků, které tvoří zásobník.</span><span class="sxs-lookup"><span data-stu-id="29279-316">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="29279-317">Každý prvek v zásobníku má svou vlastní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="29279-317">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="29279-318">Pořadí rozšíření prvků chování v chování určuje jejich pozice v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="29279-318">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="29279-319">Jako první se aplikují prvky v horní části zásobníku.</span><span class="sxs-lookup"><span data-stu-id="29279-319">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="29279-320">Postup změny řazení:</span><span class="sxs-lookup"><span data-stu-id="29279-320">To change the ordering:</span></span>

1. <span data-ttu-id="29279-321">Vyberte jeden z uzlů chování.</span><span class="sxs-lookup"><span data-stu-id="29279-321">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="29279-322">Vyberte chování, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="29279-322">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="29279-323">Vyberte prvek rozšíření chování v oddílu **pozice rozšíření chování elementu** .</span><span class="sxs-lookup"><span data-stu-id="29279-323">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>

4. <span data-ttu-id="29279-324">Chcete-li změnit pozici vybraného prvku, použijte tlačítko **nahoru** nebo **dolů** na levé straně seznamu.</span><span class="sxs-lookup"><span data-stu-id="29279-324">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="29279-325">Úprava konfigurace rozšíření prvků chování</span><span class="sxs-lookup"><span data-stu-id="29279-325">Editing the Configuration of Behavior Element Extensions</span></span>

1. <span data-ttu-id="29279-326">Vyberte jeden z uzlů chování ve stromu.</span><span class="sxs-lookup"><span data-stu-id="29279-326">Select one of the behavior nodes in the tree.</span></span>

2. <span data-ttu-id="29279-327">Vyberte chování, které obsahuje prvek, který chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="29279-327">Select the behavior that contains the element you want to edit.</span></span>

3. <span data-ttu-id="29279-328">Vyberte rozšíření prvku chování, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="29279-328">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="29279-329">Nastavení prvku se zobrazí v pravém podokně, kde je lze upravovat.</span><span class="sxs-lookup"><span data-stu-id="29279-329">The settings of the element appear in the right pane where they can be edited.</span></span>

#### <a name="protocolmapping"></a><span data-ttu-id="29279-330">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="29279-330">ProtocolMapping</span></span>

<span data-ttu-id="29279-331">V této části můžete nastavit výchozí typy vazeb pro různé protokoly, jako jsou http, TCP, MSMQ nebo NET. pipe, prostřednictvím definovaného mapování mezi schématy adres protokolů a možnými vazbami.</span><span class="sxs-lookup"><span data-stu-id="29279-331">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="29279-332">Můžete také přidat nová mapování na jiné protokoly.</span><span class="sxs-lookup"><span data-stu-id="29279-332">You can also add new mappings to other protocols.</span></span>

#### <a name="extensions"></a><span data-ttu-id="29279-333">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="29279-333">Extensions</span></span>

<span data-ttu-id="29279-334">Nová rozšíření vazby, rozšíření elementů vazby, standardní rozšíření koncových bodů a rozšíření chování lze zaregistrovat pro použití v konfiguraci služby WCF.</span><span class="sxs-lookup"><span data-stu-id="29279-334">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="29279-335">Rozšíření jsou páry název/typ.</span><span class="sxs-lookup"><span data-stu-id="29279-335">Extensions are name/type pairs.</span></span> <span data-ttu-id="29279-336">Název definuje název rozšíření v konfiguraci, zatímco typ implementuje rozšíření.</span><span class="sxs-lookup"><span data-stu-id="29279-336">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="29279-337">Existují čtyři typy rozšíření:</span><span class="sxs-lookup"><span data-stu-id="29279-337">There are four types of extensions:</span></span>

- <span data-ttu-id="29279-338">Rozšíření vazby definují celý typ vazby.</span><span class="sxs-lookup"><span data-stu-id="29279-338">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="29279-339">Příklad: `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="29279-339">Example: `basicHttpBinding`.</span></span>

- <span data-ttu-id="29279-340">Rozšíření elementu vazby definují prvek vazby.</span><span class="sxs-lookup"><span data-stu-id="29279-340">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="29279-341">Příklad: `textMessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="29279-341">Example: `textMessageEncoding`.</span></span>

- <span data-ttu-id="29279-342">Rozšíření Standard Endpoint Extensions definují celý standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="29279-342">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="29279-343">Příklad: `discoveryEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="29279-343">Example: `discoveryEndpoint`.</span></span>

- <span data-ttu-id="29279-344">Rozšíření prvků chování definují prvek chování.</span><span class="sxs-lookup"><span data-stu-id="29279-344">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="29279-345">Příklad: `clientVia`.</span><span class="sxs-lookup"><span data-stu-id="29279-345">Example: `clientVia`.</span></span>

 <span data-ttu-id="29279-346">Rozšíření, která byla registrována v konfiguraci, lze použít jako jakoukoli jinou komponentu WCF stejného typu.</span><span class="sxs-lookup"><span data-stu-id="29279-346">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>

##### <a name="adding-a-new-extension"></a><span data-ttu-id="29279-347">Přidání nového rozšíření</span><span class="sxs-lookup"><span data-stu-id="29279-347">Adding a new extension</span></span>

<span data-ttu-id="29279-348">Vyberte jeden z uzlů rozšíření v pokročilých uzlech:</span><span class="sxs-lookup"><span data-stu-id="29279-348">Select one of the extension nodes in the advanced nodes:</span></span>

1. <span data-ttu-id="29279-349">Klikněte na možnost **Nové**.</span><span class="sxs-lookup"><span data-stu-id="29279-349">Click **New**.</span></span>

2. <span data-ttu-id="29279-350">Zadejte název a typ.</span><span class="sxs-lookup"><span data-stu-id="29279-350">Enter a name and type.</span></span>

3. <span data-ttu-id="29279-351">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="29279-351">Click **OK**.</span></span>

4. <span data-ttu-id="29279-352">Rozšíření se nyní zobrazí na příslušném místě v editoru.</span><span class="sxs-lookup"><span data-stu-id="29279-352">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="29279-353">Například pokud přidáte rozšíření prvku chování, zobrazí se v seznamu dostupných rozšíření.</span><span class="sxs-lookup"><span data-stu-id="29279-353">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>

#### <a name="hosting-environment"></a><span data-ttu-id="29279-354">Hostitelské prostředí</span><span class="sxs-lookup"><span data-stu-id="29279-354">Hosting Environment</span></span>

<span data-ttu-id="29279-355">Tato část umožňuje definovat nastavení vytváření instancí pro hostitelské prostředí služby.</span><span class="sxs-lookup"><span data-stu-id="29279-355">This section allows you to define instantiation settings for the service hosting environment.</span></span>

### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="29279-356">Vytvoření konfiguračního souboru pomocí Průvodce</span><span class="sxs-lookup"><span data-stu-id="29279-356">Creating a Configuration File Using the Wizard</span></span>

<span data-ttu-id="29279-357">Jedním ze způsobů, jak vytvořit nový konfigurační soubor, je použít Průvodce novým prvkem služby.</span><span class="sxs-lookup"><span data-stu-id="29279-357">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="29279-358">Průvodce najde nainstalované typy služeb a další prvky kompatibilní s WCF v počítači, včetně virtuálních adresářů služby COM+ a webhost, a načítají je, aby bylo možné konfiguraci mnohem zefektivnit.</span><span class="sxs-lookup"><span data-stu-id="29279-358">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>

#### <a name="creating-a-configuration-file"></a><span data-ttu-id="29279-359">Vytváření konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="29279-359">Creating a Configuration File</span></span>

1. <span data-ttu-id="29279-360">Spusťte editor konfigurace služby pomocí příkazového řádku a přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe`.</span><span class="sxs-lookup"><span data-stu-id="29279-360">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="29279-361">V nabídce **soubor** vyberte **otevřít** a klikněte na **spustitelný**soubor, **službu com+** nebo **službu webhosted Service**v závislosti na typu konfiguračního souboru, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="29279-361">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>

3. <span data-ttu-id="29279-362">V dialogovém okně **otevřít** přejděte do konkrétního souboru, pro který chcete vytvořit konfigurační soubor, a dvakrát na něj klikněte.</span><span class="sxs-lookup"><span data-stu-id="29279-362">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>

4. <span data-ttu-id="29279-363">V nabídce **soubor** přejděte na příkaz **Přidat novou položku** a klikněte na možnost **Služba**.</span><span class="sxs-lookup"><span data-stu-id="29279-363">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="29279-364">Otevře se Průvodce novým prvkem služby.</span><span class="sxs-lookup"><span data-stu-id="29279-364">The New Service Element Wizard opens.</span></span>

5. <span data-ttu-id="29279-365">Pomocí kroků v průvodci vytvořte novou službu.</span><span class="sxs-lookup"><span data-stu-id="29279-365">Follow the steps in the wizard to create the new service.</span></span>

> [!NOTE]
> <span data-ttu-id="29279-366">Chcete-li použít NetPeerTcpBinding z konfiguračního souboru vygenerovaného průvodcem, je nutné ručně přidat prvek konfigurace vazby a změnit atribut `mode` jeho elementu `security` na hodnotu None.</span><span class="sxs-lookup"><span data-stu-id="29279-366">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>

## <a name="configuring-com"></a><span data-ttu-id="29279-367">Konfigurace modelu COM+</span><span class="sxs-lookup"><span data-stu-id="29279-367">Configuring COM+</span></span>

<span data-ttu-id="29279-368">Editor konfigurace služby umožňuje vytvořit nový konfigurační soubor pro existující aplikaci modelu COM+ nebo upravit existující konfiguraci modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="29279-368">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="29279-369">Uzel **kontraktu com** je zobrazen pouze v případě, že v konfiguračním souboru existuje oddíl <`comContract`>.</span><span class="sxs-lookup"><span data-stu-id="29279-369">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>

### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="29279-370">Vytváří se nová konfigurace COM+.</span><span class="sxs-lookup"><span data-stu-id="29279-370">Creating a New COM+ Configuration</span></span>

<span data-ttu-id="29279-371">Před vytvořením nové konfigurace COM+ se ujistěte, že je vaše aplikace COM+ nainstalovaná v rámci služby komponent a zaregistrovaná v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="29279-371">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>

1. <span data-ttu-id="29279-372">Výběr nabídky **soubor** – > **integraci** -> **aplikace com+.**</span><span class="sxs-lookup"><span data-stu-id="29279-372">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="29279-373">Tato operace zavře aktuální otevřený soubor.</span><span class="sxs-lookup"><span data-stu-id="29279-373">This operation closes the current opened file.</span></span> <span data-ttu-id="29279-374">Pokud se v aktuálním souboru nacházejí neuložená data, zobrazí se dialogové okno Uložit.</span><span class="sxs-lookup"><span data-stu-id="29279-374">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="29279-375">Pak se spustí **Průvodce integrací com+** .</span><span class="sxs-lookup"><span data-stu-id="29279-375">The **COM+ Integration Wizard** is then launched.</span></span>

2. <span data-ttu-id="29279-376">Na první stránce vyberte aplikaci COM+ ze stromu.</span><span class="sxs-lookup"><span data-stu-id="29279-376">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="29279-377">Pokud ve stromové struktuře nemůžete najít aplikaci modelu COM+, ověřte, zda je nainstalována do služby komponent a registrována v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="29279-377">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>

3. <span data-ttu-id="29279-378">Na další stránce vyberte, které metody chcete zveřejnit jako služby WCF.</span><span class="sxs-lookup"><span data-stu-id="29279-378">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="29279-379">Ve výchozím nastavení se zobrazí všechny podporované metody v aplikaci modelu COM+ a vybrané.</span><span class="sxs-lookup"><span data-stu-id="29279-379">All the supported methods in the COM+ application are displayed and selected by default.</span></span>

4. <span data-ttu-id="29279-380">Vyberte metodu hostování.</span><span class="sxs-lookup"><span data-stu-id="29279-380">Choose a hosting method.</span></span>

5. <span data-ttu-id="29279-381">Nakonfigurujte další nastavení podle průvodců v průvodci.</span><span class="sxs-lookup"><span data-stu-id="29279-381">Configure other settings according to the guides in the wizard.</span></span>

6. <span data-ttu-id="29279-382">Editor konfigurace služby používá ComSvcConfig. exe na pozadí ke generování konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="29279-382">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="29279-383">Po dokončení můžete zobrazit souhrn a ukončit průvodce.</span><span class="sxs-lookup"><span data-stu-id="29279-383">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="29279-384">Vygenerovaný konfigurační soubor je otevřen, aby jej bylo možné přímo upravit.</span><span class="sxs-lookup"><span data-stu-id="29279-384">The generated configuration file is opened so that you can edit it directly.</span></span>

### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="29279-385">Úprava existující konfigurace modelu COM+</span><span class="sxs-lookup"><span data-stu-id="29279-385">Editing an Existing COM+ Configuration</span></span>

1. <span data-ttu-id="29279-386">Vyberte nabídku **soubor** -> **otevřít** -> **com+** ...</span><span class="sxs-lookup"><span data-stu-id="29279-386">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>

2. <span data-ttu-id="29279-387">V seznamu vyberte službu COM+, kterou chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="29279-387">Select the COM+ Service you want to edit from the list.</span></span>

3. <span data-ttu-id="29279-388">Upravte nastavení konfigurace v uzlu **kontrakty com** .</span><span class="sxs-lookup"><span data-stu-id="29279-388">Edit configuration settings in the **COM Contracts** node.</span></span>

    > [!NOTE]
    > <span data-ttu-id="29279-389">Můžete také přímo otevřít a upravit konfigurační soubor, který obsahuje smlouvy COM.</span><span class="sxs-lookup"><span data-stu-id="29279-389">You can also directly open and edit a configuration file that contains COM contracts.</span></span>

## <a name="security"></a><span data-ttu-id="29279-390">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="29279-390">Security</span></span>

<span data-ttu-id="29279-391">Není zaručeno zabezpečení konfiguračního souboru služby vygenerovaného editorem konfigurace.</span><span class="sxs-lookup"><span data-stu-id="29279-391">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="29279-392">Informace o tom, jak zabezpečit služby WCF, najdete v dokumentaci k [zabezpečení](./feature-details/security.md) .</span><span class="sxs-lookup"><span data-stu-id="29279-392">Please refer to the [Security](./feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>

<span data-ttu-id="29279-393">Kromě toho lze editor konfigurace použít pouze ke čtení a zápisu platných konfiguračních elementů WCF.</span><span class="sxs-lookup"><span data-stu-id="29279-393">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="29279-394">Nástroj ignoruje uživatelsky definované prvky, které odpovídají schématu.</span><span class="sxs-lookup"><span data-stu-id="29279-394">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="29279-395">Nepokouší se také odebrat tyto prvky z konfiguračního souboru nebo určit jejich účinky na známé elementy WCF.</span><span class="sxs-lookup"><span data-stu-id="29279-395">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="29279-396">Je zodpovědností uživatele určit, zda tyto prvky představují hrozbu pro aplikaci nebo systém.</span><span class="sxs-lookup"><span data-stu-id="29279-396">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
