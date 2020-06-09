---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: d64be95f71f840e08ede63e1c1f14ee08e52ce97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592473"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="3c23a-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="3c23a-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="3c23a-103">ConfigurationCodeGenerator je nástroj, který můžete použít k vystavení vlastních implementací kanálu do konfiguračního systému.</span><span class="sxs-lookup"><span data-stu-id="3c23a-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="3c23a-104">To umožňuje uživatelům vašeho vlastního kanálu nakonfigurovat svůj kanál pomocí souboru. config stejným způsobem, jako by nakonfigurovali systémově poskytované vazby, jako je například `NetTcpBinding` nebo vlastní vazba pomocí `TcpTransportBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="3c23a-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="3c23a-105">Při psaní vlastního kanálu a jeho zpřístupnění pro programovací model pomocí nového `BindingElement` nebo `Binding` , je nutné vytvořit sadu tříd pro vytvoření `BindingElement` nebo `Binding` konfiguraci pomocí souboru. config.</span><span class="sxs-lookup"><span data-stu-id="3c23a-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="3c23a-106">Pomocí nástroje ConfigurationCodeGenerator můžete tyto třídy vygenerovat a rozšířit možnosti svého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="3c23a-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="3c23a-107">Sestavení nástroje</span><span class="sxs-lookup"><span data-stu-id="3c23a-107">To build the tool</span></span>  
  
1. <span data-ttu-id="3c23a-108">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c23a-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="3c23a-109">Sestavení řešení generuje jeden soubor: ConfigurationCodeGenerator. exe.</span><span class="sxs-lookup"><span data-stu-id="3c23a-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="3c23a-110">Soubor SampleRun. cmd obsahuje vzorový příkazový řádek, který ukazuje, jak tento nástroj použít k vygenerování tříd pro příklad [Transport: UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="3c23a-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="3c23a-111">Spuštění nástroje</span><span class="sxs-lookup"><span data-stu-id="3c23a-111">To run the tool</span></span>  
  
1. <span data-ttu-id="3c23a-112">Pokud máte vlastní `BindingElement` typ i vlastní typ, zadejte na příkazovém řádku následující příkaz `Binding` :</span><span class="sxs-lookup"><span data-stu-id="3c23a-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="3c23a-113">Pokud máte pouze vlastní typ, zadejte následující `BindingElement` :</span><span class="sxs-lookup"><span data-stu-id="3c23a-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="3c23a-114">Pokud máte pouze vlastní typ, zadejte následující `Binding` :</span><span class="sxs-lookup"><span data-stu-id="3c23a-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="3c23a-115">Příkaz vygeneruje tři soubory. cs pro `BindingElement` (Pokud jste zadali možnost/BE:), pět souborů cs pro standardní `Binding` (Pokud jste zadali možnost/Sb:) a souboru. XML.</span><span class="sxs-lookup"><span data-stu-id="3c23a-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="3c23a-116">Pokud jste použili možnost/BE, jeden ze souborů. cs implementuje rozhraní `BindingElementExtensionSection` pro váš element vazby.</span><span class="sxs-lookup"><span data-stu-id="3c23a-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="3c23a-117">Tento kód zpřístupňuje `BindingElement` systém konfigurace, aby ostatní vlastní vazby mohly použít váš element vazby.</span><span class="sxs-lookup"><span data-stu-id="3c23a-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="3c23a-118">Ostatní soubory mají třídy, které reprezentují výchozí hodnoty a konstanty.</span><span class="sxs-lookup"><span data-stu-id="3c23a-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="3c23a-119">Soubory obsahují komentáře, které vám umožní `//TODO` připomenout, abyste aktualizovali výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3c23a-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="3c23a-120">Pokud jste zadali možnost/Sb, dva ze souborů. cs implementují a v `StandardBindingElement` `StandardBindingCollectionElement` uvedeném pořadí zpřístupňují standardní vazbu na konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="3c23a-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="3c23a-121">Ostatní soubory mají třídy, které reprezentují výchozí hodnoty a konstanty.</span><span class="sxs-lookup"><span data-stu-id="3c23a-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="3c23a-122">Soubory obsahují komentáře, které vám umožní `//TODO` připomenout, abyste aktualizovali výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3c23a-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="3c23a-123">Pokud jste zadali možnost/Sb: parametr CodeToAddTo \<*YourStdBinding*> . cs obsahuje kód, který musíte ručně přidat do třídy, která implementuje standardní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3c23a-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="3c23a-124">Soubor SampleConfig. XML obsahuje konfigurační kód, který je nutné přidat do konfiguračního souboru, který registruje obslužné rutiny definované v předchozích krocích 1 nebo 2.</span><span class="sxs-lookup"><span data-stu-id="3c23a-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
