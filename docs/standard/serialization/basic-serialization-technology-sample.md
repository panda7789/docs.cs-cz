---
title: Ukázka technologie základní serializace
description: Tato ukázka předvádí možnost CLR k serializaci grafu objektů v paměti do datového proudu. Tato ukázka může používat SoapFormatter nebo BinaryFormatter.
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 3f2273e6afb3a72f9734444ffe92d30871fb762b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276566"
---
# <a name="basic-serialization-technology-sample"></a>Ukázka technologie základní serializace

[Stažení ukázky](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)

Tento příklad znázorňuje možnost common language runtime k serializaci grafu objektů v paměti do datového proudu. V tomto příkladu můžete použít buď <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pro serializaci. Odkazovaného seznamu, vyplněno data, je serializován nebo deserializován nebo z datový proud souboru. V obou případech se zobrazí v seznamu, aby mohli zobrazit výsledky. Propojený seznam je typu `LinkedList`, typu definované v tomto příkladu.

Komentáře v souborech zdrojového kódu a build.proj Další informace o serializaci.

### <a name="to-build-the-sample-using-the-command-prompt"></a>K vytvoření vzorku pomocí příkazového řádku

1. Přejděte do jednoho podadresáře konkrétní jazyk do adresáře Technologies\Serialization\Runtime Serialization\Basic, pomocí příkazového řádku.

2. Do příkazového řádku zadejte **MSBuild SerializationCS. sln**, **MSBuild SerializationJSL. sln** nebo **MSBuild SerializationVB. sln**v závislosti na zvoleném programovacím jazyce.

### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio

1. Otevřete Průzkumníka souborů a přejděte do jednoho podadresáře konkrétní jazyk pro ukázku.

2. Poklepejte na ikonu souboru SerializationCS.sln, SerializationJSL.sln nebo SerializationVB.sln podle svého výběru: programovací jazyk, k otevření souboru v sadě Visual Studio.

3. V nabídce **sestavení** vyberte **Sestavit řešení**.

 Vzorová aplikace bude vytvořen v podadresáři \bin nebo \bin\Debug výchozí.

### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

1. Přejděte do adresáře, který obsahuje připravené spustitelný soubor.

2. Do příkazového řádku zadejte **Serialization. exe**, spolu s hodnotami parametrů, které si přejete.

  > [!NOTE]
  > Tato ukázka vytvoří aplikace konzoly. Musí spusťte ji pomocí příkazového řádku, aby bylo možné zobrazit její výsledek.

## <a name="remarks"></a>Poznámky

Ukázkové aplikace, který přijme parametry příkazového řádku, která určuje, které můžete testovat se má provést. Chcete-li serializovat seznam 10 uzlů do souboru s názvem **test. XML** pomocí formátovacího modulu SOAP, použijte parametry **SX test. XML 10**.

Příklad:

```console
Serialize.exe -sx Test.xml 10
```

Chcete-li deserializovat soubor **test. XML** z předchozího příkladu, použijte parametry **DX test. XML**.

Příklad:

```console
Serialize.exe -dx Test.xml
```

V obou výše uvedených příkladech "x" v přepínačem příkazového řádku udává, že serializace XML SOAP. "B" můžete místo ní používat binární serializace. Pokud chcete akci serializace s velmi velkým počtem uzlů, můžete chtít přesměrovat výstup konzoly do souboru.

Příklad:

```console
Serialize.exe -sb Test.bin 10000 >somefile.txt
```

Následující odrážky Krátce popište, třídy a technologie používané v tomto příkladu.

- Modul runtime serializace

  - <xref:System.Runtime.Serialization.IFormatter>Slouží k odkazování na <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> objekt nebo.

  - <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Slouží k serializaci propojeného seznamu do datového proudu v binárním formátu. Binární formátovací modul používá formát pouze <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> znalost typu. Data jsou však stručné.

  - <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Slouží k serializaci propojeného seznamu do datového proudu ve formátu SOAP. Protokol SOAP je ve standardním formátu.

- I/O proudu

  - <xref:System.IO.Stream>Používá se k serializaci a deserializaci. Typ konkrétní datového proudu, který je použit v tomto příkladu je <xref:System.IO.FileStream> typu. Serializace však lze používat s libovolného typu odvozeného z <xref:System.IO.Stream>.

  - <xref:System.IO.File>Slouží k vytváření <xref:System.IO.FileStream> objektů pro čtení a vytváření souborů na disku.

  - <xref:System.IO.FileStream>Slouží k serializaci a deserializaci propojených seznamů.

## <a name="see-also"></a>Viz také

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
- [Základní serializace](basic-serialization.md)
- [Binární serializace](binary-serialization.md)
- [Řízení serializace XML pomocí atributů](controlling-xml-serialization-using-attributes.md)
- [Představení serializace XML](introducing-xml-serialization.md)
- [Serializace](index.md)
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
