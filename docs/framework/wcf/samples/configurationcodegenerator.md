---
title: ConfigurationCodeGenerator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb88d7e523c671886e3ccb0fe22d545c616e2289
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="d0dfb-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="d0dfb-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="d0dfb-103">ConfigurationCodeGenerator je nástroj, který můžete použít ke zveřejnění vaší implementace vlastní kanál konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="d0dfb-104">To umožňuje uživatelům vlastní kanál nakonfigurovat kanál pomocí souboru .config stejně, jako by nakonfigurovat poskytované systémem vazbu, jako `NetTcpBinding` nebo vlastní vazby pomocí `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="d0dfb-105">Při zápisu vlastním kanálu a umístěte ji do programovací model pomocí nové `BindingElement` nebo `Binding`, musíte vytvořit sadu tříd, aby `BindingElement` nebo `Binding` možné konfigurovat pomocí souboru .config.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="d0dfb-106">Nástroj ConfigurationCodeGenerator můžete vygenerovat tyto třídy a zajištění lepších možností vašeho zákazníka.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="d0dfb-107">K sestavení nástroje</span><span class="sxs-lookup"><span data-stu-id="d0dfb-107">To build the tool</span></span>  
  
1.  <span data-ttu-id="d0dfb-108">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0dfb-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="d0dfb-109">Sestavování řešení generuje jeden soubor: ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="d0dfb-110">Soubor SampleRun.cmd má ukázka příkazového řádku, který ukazuje, jak tento nástroj používat ke generování tříd [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="d0dfb-111">Chcete-li spustit nástroj</span><span class="sxs-lookup"><span data-stu-id="d0dfb-111">To run the tool</span></span>  
  
1.  <span data-ttu-id="d0dfb-112">Na příkazovém řádku zadejte následující, pokud máte i vlastní `BindingElement` typ a vlastní `Binding` typu:</span><span class="sxs-lookup"><span data-stu-id="d0dfb-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="d0dfb-113">Nebo zadejte následující příkaz, pokud máte pouze vlastní `BindingElement` typu:</span><span class="sxs-lookup"><span data-stu-id="d0dfb-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="d0dfb-114">Nebo zadejte následující příkaz, pokud máte pouze vlastní `Binding` typu:</span><span class="sxs-lookup"><span data-stu-id="d0dfb-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="d0dfb-115">Příkaz generuje tři soubory .cs pro `BindingElement` (Pokud jste zadali / být: možnost), pět souborů .cs pro standardní `Binding` (Pokud jste zadali /sb: možnost) a souboru .xml.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1.  <span data-ttu-id="d0dfb-116">Pokud jste použili možnost /be, jeden .cs soubory implementuje `BindingElementExtensionSection` pro vaše prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="d0dfb-117">Tento kód zpřístupní vaše `BindingElement` konfigurace systému, můžete použít, aby další vlastní vazby vaší prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="d0dfb-118">Ostatní soubory mají tříd, které představují výchozí hodnoty a konstanty.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="d0dfb-119">U souborů `//TODO` komentáře a tak poznáte, chcete-li aktualizovat výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2.  <span data-ttu-id="d0dfb-120">Pokud jste zadali možnost /sb, dva soubory .cs implementovat `StandardBindingElement` a `StandardBindingCollectionElement` , který zpřístupňuje vaše standardní vazby v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="d0dfb-121">Ostatní soubory mají tříd, které představují výchozí hodnoty a konstanty.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="d0dfb-122">U souborů `//TODO` komentáře a tak poznáte, chcete-li aktualizovat výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="d0dfb-123">Pokud jste zadali /sb: možnost CodeToAddTo\<*YourStdBinding*> .cs má kód, který je třeba ručně přidat do třídy, který implementuje standardní vazbě.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="d0dfb-124">Soubor SampleConfig.xml obsahuje kód konfigurace, které je nutné přidat do konfiguračního souboru, který registruje obslužné rutiny definované v předchozím kroku, 1 nebo 2.</span><span class="sxs-lookup"><span data-stu-id="d0dfb-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0dfb-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0dfb-125">See Also</span></span>
