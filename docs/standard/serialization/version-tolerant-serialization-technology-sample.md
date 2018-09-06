---
title: Ukázka technologie serializace tolerantní vůči verzím verze
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 34dccc9065c0100a01a7969a1fe762001e2999a9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866420"
---
# <a name="version-tolerant-serialization-technology-sample"></a>Ukázka technologie serializace tolerantní vůči verzím verze
[Stáhněte si ukázky](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 Tento příklad znázorňuje verze funkce tolerance serializace rozhraní .NET. Ukázka sestavení aplikace, které používají různé verze <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> k serializaci a deserializaci data. Bez ohledu na přítomnost jiný typ verze aplikace komunikovat bez problémů. Další informace najdete v tématu [serializace tolerantní vůči verzím verze](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>K vytvoření vzorku pomocí příkazového řádku  
  
1.  Otevřete okno příkazového řádku a přejděte do jednoho podadresáře konkrétní jazyk (v rámci aplikace V1 nebo V2 aplikace) pro vzorku.  
  
2.  Typ **msbuild.exe \<verů > application.sln** příkazového řádku (kde \<verů > je v1 nebo v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio  
  
1.  Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.  
  
2.  Přejděte do aplikace V1 podadresáře adresáře, který jste vybrali v předchozím kroku.  
  
3.  Poklepejte na ikonu V1 Application.sln k otevření souboru v sadě Visual Studio.  
  
4.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
5.  Přejděte do podadresáře V2 aplikace a opakujte předchozí dva kroky pro vytvoření aplikace V2.  
  
 Aplikace bude vytvořen v výchozí \bin nebo \bin\Debug podadresářích adresáře jejich příslušného projektu.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  V okně příkazového řádku přejděte na konkrétní jazyk podadresář, který jste vybrali, když jste vytvořili ukázkové aplikace.  
  
2.  Typ **runme.cmd** na příkazovém řádku spusťte obě aplikace najednou.  
  
 Alternativně přejděte do adresáře, které obsahují nové spustitelné soubory a spustit je postupně.  
  
> [!NOTE]
>  Ukázka sestavení aplikace konzoly. Je nutné spustit a spustit v okně příkazového řádku, chcete-li zobrazit jejich výstup.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
- <xref:System.IO.FileStream>
