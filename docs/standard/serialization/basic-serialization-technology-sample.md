---
title: Ukázka technologie základní serializace
description: Tato ukázka předvádí možnost CLR k serializaci grafu objektů v paměti do datového proudu. Tato ukázka může používat SoapFormatter nebo BinaryFormatter.
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: fcbf790c3b3d48a0aeb27fd1ef6f75dcd7609ae0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378431"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="6d9d3-104">Ukázka technologie základní serializace</span><span class="sxs-lookup"><span data-stu-id="6d9d3-104">Basic Serialization Technology Sample</span></span>

[<span data-ttu-id="6d9d3-105">Stažení ukázky</span><span class="sxs-lookup"><span data-stu-id="6d9d3-105">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)

<span data-ttu-id="6d9d3-106">Tento příklad znázorňuje možnost common language runtime k serializaci grafu objektů v paměti do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-106">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="6d9d3-107">V tomto příkladu můžete použít buď <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-107">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="6d9d3-108">Odkazovaného seznamu, vyplněno data, je serializován nebo deserializován nebo z datový proud souboru.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-108">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="6d9d3-109">V obou případech se zobrazí v seznamu, aby mohli zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-109">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="6d9d3-110">Propojený seznam je typu `LinkedList`, typu definované v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-110">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>

<span data-ttu-id="6d9d3-111">Komentáře v souborech zdrojového kódu a build.proj Další informace o serializaci.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-111">Review comments in the source code and build.proj files for more information on serialization.</span></span>

### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="6d9d3-112">K vytvoření vzorku pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6d9d3-112">To build the sample using the Command Prompt</span></span>

1. <span data-ttu-id="6d9d3-113">Přejděte do jednoho podadresáře konkrétní jazyk do adresáře Technologies\Serialization\Runtime Serialization\Basic, pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-113">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>

2. <span data-ttu-id="6d9d3-114">Do příkazového řádku zadejte **MSBuild SerializationCS. sln**, **MSBuild SerializationJSL. sln** nebo **MSBuild SerializationVB. sln**v závislosti na zvoleném programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-114">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>

### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="6d9d3-115">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6d9d3-115">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="6d9d3-116">Otevřete Průzkumníka souborů a přejděte do jednoho podadresáře konkrétní jazyk pro ukázku.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-116">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>

2. <span data-ttu-id="6d9d3-117">Poklepejte na ikonu souboru SerializationCS.sln, SerializationJSL.sln nebo SerializationVB.sln podle svého výběru: programovací jazyk, k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-117">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="6d9d3-118">V nabídce **sestavení** vyberte **Sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-118">In the **Build** menu, select **Build Solution**.</span></span>

 <span data-ttu-id="6d9d3-119">Vzorová aplikace bude vytvořen v podadresáři \bin nebo \bin\Debug výchozí.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-119">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>

### <a name="to-run-the-sample"></a><span data-ttu-id="6d9d3-120">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="6d9d3-120">To run the sample</span></span>

1. <span data-ttu-id="6d9d3-121">Přejděte do adresáře, který obsahuje připravené spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-121">Navigate to the directory containing the built executable.</span></span>

2. <span data-ttu-id="6d9d3-122">Do příkazového řádku zadejte **Serialization. exe**, spolu s hodnotami parametrů, které si přejete.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-122">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6d9d3-123">Tato ukázka vytvoří aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-123">This sample builds a console application.</span></span> <span data-ttu-id="6d9d3-124">Musí spusťte ji pomocí příkazového řádku, aby bylo možné zobrazit její výsledek.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-124">You must launch it using the command prompt in order to view its output.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d9d3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d9d3-125">Remarks</span></span>

<span data-ttu-id="6d9d3-126">Ukázkové aplikace, který přijme parametry příkazového řádku, která určuje, které můžete testovat se má provést.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-126">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="6d9d3-127">Chcete-li serializovat seznam 10 uzlů do souboru s názvem **test. XML** pomocí formátovacího modulu SOAP, použijte parametry **SX test. XML 10**.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-127">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>

<span data-ttu-id="6d9d3-128">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6d9d3-128">For Example:</span></span>

```console
Serialize.exe -sx Test.xml 10
```

<span data-ttu-id="6d9d3-129">Chcete-li deserializovat soubor **test. XML** z předchozího příkladu, použijte parametry **DX test. XML**.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-129">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>

<span data-ttu-id="6d9d3-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6d9d3-130">For Example:</span></span>

```console
Serialize.exe -dx Test.xml
```

<span data-ttu-id="6d9d3-131">V obou výše uvedených příkladech "x" v přepínačem příkazového řádku udává, že serializace XML SOAP.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="6d9d3-132">"B" můžete místo ní používat binární serializace.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="6d9d3-133">Pokud chcete akci serializace s velmi velkým počtem uzlů, můžete chtít přesměrovat výstup konzoly do souboru.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>

<span data-ttu-id="6d9d3-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6d9d3-134">For Example:</span></span>

```console
Serialize.exe -sb Test.bin 10000 >somefile.txt
```

<span data-ttu-id="6d9d3-135">Následující odrážky Krátce popište, třídy a technologie používané v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-135">The following bullets briefly describe the classes and technologies used by this sample.</span></span>

- <span data-ttu-id="6d9d3-136">Modul runtime serializace</span><span class="sxs-lookup"><span data-stu-id="6d9d3-136">Runtime Serialization</span></span>

  - <span data-ttu-id="6d9d3-137"><xref:System.Runtime.Serialization.IFormatter>Slouží k odkazování na <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> objekt nebo.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-137"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>

  - <span data-ttu-id="6d9d3-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Slouží k serializaci propojeného seznamu do datového proudu v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="6d9d3-139">Binární formátovací modul používá formát pouze <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> znalost typu.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-139">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="6d9d3-140">Data jsou však stručné.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-140">However, the data is concise.</span></span>

  - <span data-ttu-id="6d9d3-141"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Slouží k serializaci propojeného seznamu do datového proudu ve formátu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-141"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="6d9d3-142">Protokol SOAP je ve standardním formátu.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-142">SOAP is a standard format.</span></span>

- <span data-ttu-id="6d9d3-143">I/O proudu</span><span class="sxs-lookup"><span data-stu-id="6d9d3-143">Stream I/O</span></span>

  - <span data-ttu-id="6d9d3-144"><xref:System.IO.Stream>Používá se k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-144"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="6d9d3-145">Typ konkrétní datového proudu, který je použit v tomto příkladu je <xref:System.IO.FileStream> typu.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-145">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="6d9d3-146">Serializace však lze používat s libovolného typu odvozeného z <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-146">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>

  - <span data-ttu-id="6d9d3-147"><xref:System.IO.File>Slouží k vytváření <xref:System.IO.FileStream> objektů pro čtení a vytváření souborů na disku.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-147"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>

  - <span data-ttu-id="6d9d3-148"><xref:System.IO.FileStream>Slouží k serializaci a deserializaci propojených seznamů.</span><span class="sxs-lookup"><span data-stu-id="6d9d3-148"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d9d3-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d9d3-149">See also</span></span>

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
- [<span data-ttu-id="6d9d3-150">Základní serializace</span><span class="sxs-lookup"><span data-stu-id="6d9d3-150">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="6d9d3-151">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="6d9d3-151">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="6d9d3-152">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="6d9d3-152">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="6d9d3-153">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="6d9d3-153">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="6d9d3-154">Serializace</span><span class="sxs-lookup"><span data-stu-id="6d9d3-154">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="6d9d3-155">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="6d9d3-155">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
