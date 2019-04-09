---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: 7625060cd0512bb7498a931d7b93a731e52c9f00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195186"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="12341-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="12341-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="12341-103">ConfigurationCodeGenerator je nástroj, který můžete použít ke zveřejnění vašeho vlastního kanálu implementace konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="12341-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="12341-104">To umožňuje uživatelům vlastní kanál konfigurovat kanál pomocí souboru .config, stejně jako poskytnutými systémem vazby, jako by konfigurace `NetTcpBinding` nebo vlastní vazby pomocí `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="12341-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="12341-105">Při zápisu vlastního kanálu a zpřístupnit ji programovací model s použitím nového `BindingElement` nebo `Binding`, musíte vytvořit sadu tříd, aby `BindingElement` nebo `Binding` umožňovat konfiguraci pomocí souboru .config.</span><span class="sxs-lookup"><span data-stu-id="12341-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="12341-106">Nástroj ConfigurationCodeGenerator můžete použít ke generování těchto tříd a vylepšení prostředí pro vaše zákazníky.</span><span class="sxs-lookup"><span data-stu-id="12341-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="12341-107">K sestavení nástroj</span><span class="sxs-lookup"><span data-stu-id="12341-107">To build the tool</span></span>  
  
1.  <span data-ttu-id="12341-108">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="12341-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="12341-109">Sestavování řešení se generuje jeden soubor: ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="12341-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="12341-110">Ukázka příkazového řádku, který ukazuje, jak tento nástroj používat ke generování třídy pro má soubor SampleRun.cmd [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="12341-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="12341-111">Chcete-li spustit nástroj</span><span class="sxs-lookup"><span data-stu-id="12341-111">To run the tool</span></span>  
  
1.  <span data-ttu-id="12341-112">Na příkazovém řádku zadejte následující, pokud máte i vlastní `BindingElement` typu a vlastní `Binding` typu:</span><span class="sxs-lookup"><span data-stu-id="12341-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="12341-113">Nebo zadejte následující příkaz, pokud máte jenom vlastní `BindingElement` typu:</span><span class="sxs-lookup"><span data-stu-id="12341-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="12341-114">Nebo zadejte následující příkaz, pokud máte jenom vlastní `Binding` typu:</span><span class="sxs-lookup"><span data-stu-id="12341-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="12341-115">Příkaz generuje pro tři soubory .cs `BindingElement` (Pokud jste zadali / být: možnost), pět souborů .cs standardu `Binding` (Pokud jste zadali /sb: možnost) a souboru .xml.</span><span class="sxs-lookup"><span data-stu-id="12341-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1.  <span data-ttu-id="12341-116">Pokud jste použili možnost /be, jeden z cs soubory implementuje `BindingElementExtensionSection` pro vaše element vazby.</span><span class="sxs-lookup"><span data-stu-id="12341-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="12341-117">Tento kód poskytuje vaše `BindingElement` konfigurace systému, aby další vlastní vazby můžete použít vaše element vazby.</span><span class="sxs-lookup"><span data-stu-id="12341-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="12341-118">Třídy, které představují výchozí hodnoty a konstanty mají jiné soubory.</span><span class="sxs-lookup"><span data-stu-id="12341-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="12341-119">U souborů `//TODO` komentáře vám aktualizovat výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="12341-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2.  <span data-ttu-id="12341-120">Pokud jste určili možnost /sb, dva soubory .cs implementovat `StandardBindingElement` a `StandardBindingCollectionElement` , která zveřejní vaše standardní vazby na konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="12341-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="12341-121">Třídy, které představují výchozí hodnoty a konstanty mají jiné soubory.</span><span class="sxs-lookup"><span data-stu-id="12341-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="12341-122">U souborů `//TODO` komentáře vám aktualizovat výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="12341-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="12341-123">Pokud jste zadali /sb: možnost CodeToAddTo\<*YourStdBinding*> .cs obsahuje kód, který je třeba ručně přidat do třídy, která implementuje standardní vazbu.</span><span class="sxs-lookup"><span data-stu-id="12341-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="12341-124">SampleConfig.xml soubor obsahuje kód konfigurace, který je nutné přidat do konfiguračního souboru, který registruje obslužné rutiny definované v předchozím kroku 1 nebo 2.</span><span class="sxs-lookup"><span data-stu-id="12341-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
