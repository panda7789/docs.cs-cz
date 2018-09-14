---
title: Ukázka technologie základní serializace
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 474eb8ded01a72182533a6d49397d7567447d64e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45619091"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="44443-102">Ukázka technologie základní serializace</span><span class="sxs-lookup"><span data-stu-id="44443-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="44443-103">Stáhněte si ukázky</span><span class="sxs-lookup"><span data-stu-id="44443-103">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="44443-104">Tento příklad znázorňuje možnost common language runtime k serializaci grafu objektů v paměti do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="44443-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="44443-105">V tomto příkladu můžete použít buď <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="44443-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="44443-106">Odkazovaného seznamu, vyplněno data, je serializován nebo deserializován nebo z datový proud souboru.</span><span class="sxs-lookup"><span data-stu-id="44443-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="44443-107">V obou případech se zobrazí v seznamu, aby mohli zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="44443-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="44443-108">Propojený seznam je typu `LinkedList`, typu definované v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="44443-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="44443-109">Komentáře v souborech zdrojového kódu a build.proj Další informace o serializaci.</span><span class="sxs-lookup"><span data-stu-id="44443-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="44443-110">K vytvoření vzorku pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="44443-110">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="44443-111">Přejděte do jednoho podadresáře konkrétní jazyk do adresáře Technologies\Serialization\Runtime Serialization\Basic, pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="44443-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="44443-112">Typ **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** nebo **msbuild SerializationVB.sln**, v závislosti na požadovaném programovací jazyk, v příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="44443-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="44443-113">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="44443-113">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="44443-114">Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="44443-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="44443-115">Poklepejte na ikonu souboru SerializationCS.sln, SerializationJSL.sln nebo SerializationVB.sln podle svého výběru: programovací jazyk, k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44443-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="44443-116">V **sestavení** nabídce vyberte možnost **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="44443-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="44443-117">Vzorová aplikace bude vytvořen v podadresáři \bin nebo \bin\Debug výchozí.</span><span class="sxs-lookup"><span data-stu-id="44443-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="44443-118">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="44443-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="44443-119">Přejděte do adresáře, který obsahuje připravené spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="44443-119">Navigate to the directory containing the built executable.</span></span>  
  
2.  <span data-ttu-id="44443-120">Typ **Serialization.exe**, spolu s hodnotami parametrů vyžadujete, na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="44443-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44443-121">Tato ukázka vytvoří aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="44443-121">This sample builds a console application.</span></span> <span data-ttu-id="44443-122">Musí spusťte ji pomocí příkazového řádku, aby bylo možné zobrazit její výsledek.</span><span class="sxs-lookup"><span data-stu-id="44443-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44443-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44443-123">Remarks</span></span>  
 <span data-ttu-id="44443-124">Ukázkové aplikace, který přijme parametry příkazového řádku, která určuje, které můžete testovat se má provést.</span><span class="sxs-lookup"><span data-stu-id="44443-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="44443-125">K serializaci seznam 10 uzel do souboru s názvem **Test.xml** pomocí formátovacího modulu protokolu SOAP, použijte parametry **sx Test.xml 10**.</span><span class="sxs-lookup"><span data-stu-id="44443-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="44443-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="44443-126">For Example:</span></span>  
  
 <span data-ttu-id="44443-127">**Serialize.exe - sx Test.xml 10**</span><span class="sxs-lookup"><span data-stu-id="44443-127">**Serialize.exe -sx Test.xml 10**</span></span>  
  
 <span data-ttu-id="44443-128">K deserializaci **Test.xml** soubor z předchozího příkladu, použijte parametry **dx Test.xml**.</span><span class="sxs-lookup"><span data-stu-id="44443-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="44443-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="44443-129">For Example:</span></span>  
  
 <span data-ttu-id="44443-130">**Serialize.exe - dx Test.xml**</span><span class="sxs-lookup"><span data-stu-id="44443-130">**Serialize.exe -dx Test.xml**</span></span>  
  
 <span data-ttu-id="44443-131">V obou výše uvedených příkladech "x" v přepínačem příkazového řádku udává, že serializace XML SOAP.</span><span class="sxs-lookup"><span data-stu-id="44443-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="44443-132">"B" můžete místo ní používat binární serializace.</span><span class="sxs-lookup"><span data-stu-id="44443-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="44443-133">Pokud chcete akci serializace s velmi velkým počtem uzlů, můžete chtít přesměrovat výstup konzoly do souboru.</span><span class="sxs-lookup"><span data-stu-id="44443-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="44443-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="44443-134">For Example:</span></span>  
  
 <span data-ttu-id="44443-135">**Serialize.exe - sb Test.bin 10000 > somefile.txt**</span><span class="sxs-lookup"><span data-stu-id="44443-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span></span>  
  
 <span data-ttu-id="44443-136">Následující odrážky Krátce popište, třídy a technologie používané v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="44443-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
-   <span data-ttu-id="44443-137">Modul runtime serializace</span><span class="sxs-lookup"><span data-stu-id="44443-137">Runtime Serialization</span></span>  
  
    -   <span data-ttu-id="44443-138"><xref:System.Runtime.Serialization.IFormatter>Slouží k odkazu na buď <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> objektu.</span><span class="sxs-lookup"><span data-stu-id="44443-138"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    -   <span data-ttu-id="44443-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Slouží k serializaci odkazovaného seznamu do datového proudu v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="44443-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="44443-140">Binární formátovací modul používá formát pouze <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> znalost typu.</span><span class="sxs-lookup"><span data-stu-id="44443-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="44443-141">Data jsou však stručné.</span><span class="sxs-lookup"><span data-stu-id="44443-141">However, the data is concise.</span></span>  
  
    -   <span data-ttu-id="44443-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Slouží k serializaci odkazovaného seznamu do datového proudu ve formátu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="44443-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="44443-143">Protokol SOAP je ve standardním formátu.</span><span class="sxs-lookup"><span data-stu-id="44443-143">SOAP is a standard format.</span></span>  
  
-   <span data-ttu-id="44443-144">I/O proudu</span><span class="sxs-lookup"><span data-stu-id="44443-144">Stream I/O</span></span>  
  
    -   <span data-ttu-id="44443-145"><xref:System.IO.Stream>Slouží k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="44443-145"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="44443-146">Typ konkrétní datového proudu, který je použit v tomto příkladu je <xref:System.IO.FileStream> typu.</span><span class="sxs-lookup"><span data-stu-id="44443-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="44443-147">Serializace však lze používat s libovolného typu odvozeného z <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="44443-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    -   <span data-ttu-id="44443-148"><xref:System.IO.File>Slouží k vytvoření <xref:System.IO.FileStream> objektů pro čtení a vytváření souborů na disku.</span><span class="sxs-lookup"><span data-stu-id="44443-148"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    -   <span data-ttu-id="44443-149"><xref:System.IO.FileStream>Slouží k serializaci a deserializaci propojené seznamy.</span><span class="sxs-lookup"><span data-stu-id="44443-149"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44443-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44443-150">See also</span></span>

- <xref:System.IO>  
- <xref:System.IO.File>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.Stream>  
- <xref:System.Random>  
- <xref:System.Runtime.Serialization>  
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
- <xref:System.Runtime.Serialization.IFormatter>  
- <xref:System.SerializableAttribute>  
- <xref:System.Xml.Serialization>  
- [<span data-ttu-id="44443-151">Základní serializace</span><span class="sxs-lookup"><span data-stu-id="44443-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
- [<span data-ttu-id="44443-152">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="44443-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
- [<span data-ttu-id="44443-153">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="44443-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [<span data-ttu-id="44443-154">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="44443-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [<span data-ttu-id="44443-155">Serializace</span><span class="sxs-lookup"><span data-stu-id="44443-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
- [<span data-ttu-id="44443-156">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="44443-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
