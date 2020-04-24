---
title: Ukázka technologie serializace tolerantní vůči verzím
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 317a47d46b839417e01eed9deca2459a96aaa201
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960783"
---
# <a name="version-tolerant-serialization-technology-sample"></a>Ukázka technologie serializace tolerantní vůči verzím
[Ukázka stažení](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 Tento příklad znázorňuje verze funkce tolerance serializace rozhraní .NET. Ukázka sestavení aplikace, které používají různé verze <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> k serializaci a deserializaci data. Bez ohledu na přítomnost jiný typ verze aplikace komunikovat bez problémů. Další informace najdete v tématu [serializace odolná proti verzi](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>K vytvoření vzorku pomocí příkazového řádku  
  
1. Otevřete okno příkazového řádku a přejděte do jednoho podadresáře konkrétní jazyk (v rámci aplikace V1 nebo V2 aplikace) pro vzorku.  
  
2. Do příkazového řádku zadejte **MSBuild. exe \<ver> Application. sln** (kde \<ver> je v1 nebo v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio  
  
1. Otevřete Průzkumníka souborů a přejděte do jednoho podadresáře konkrétní jazyk pro ukázku.  
  
2. Přejděte do aplikace V1 podadresáře adresáře, který jste vybrali v předchozím kroku.  
  
3. Poklepejte na ikonu V1 Application.sln k otevření souboru v sadě Visual Studio.  
  
4. V nabídce **Sestavení** klikněte na **Sestavit řešení**.  
  
5. Přejděte do podadresáře V2 aplikace a opakujte předchozí dva kroky pro vytvoření aplikace V2.  
  
 Aplikace bude vytvořen v výchozí \bin nebo \bin\Debug podadresářích adresáře jejich příslušného projektu.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. V okně příkazového řádku přejděte na konkrétní jazyk podadresář, který jste vybrali, když jste vytvořili ukázkové aplikace.  
  
2. Do příkazového řádku zadejte **RunMe. cmd** a spusťte obě aplikace současně.  
  
 Alternativně přejděte do adresáře, které obsahují nové spustitelné soubory a spustit je postupně.  
  
> [!NOTE]
> Ukázka sestavení aplikace konzoly. Je nutné spustit a spustit v okně příkazového řádku, chcete-li zobrazit jejich výstup.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
