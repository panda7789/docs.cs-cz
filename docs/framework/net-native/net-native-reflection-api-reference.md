---
title: Informace o rozhraní API reflexe .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a2a27f788fa84c41ccb818266fffc816237bb48
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486945"
---
# <a name="net-native-reflection-api-reference"></a>Informace o rozhraní API reflexe .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] zahrnuje tři nové typy výjimek: [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), a [ System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Mějte na paměti následující skutečnosti související všechny výjimky tři typy:  
  
 Tyto typy jsou pouze pro interní použití.  
 Tyto typy tři výjimek jsou pro použití [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce. Výjimky jsou vyvolány při [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězce nástrojů rozpozná chybějící data, která neumožňuje pokračovat v provádění programu.  
  
 Ke zpracování těchto výjimek v kódu.  
 Tyto výjimky signalizují, obou těchto metadat, které vaše aplikace vyžaduje chybí ( [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky) nebo že implementační kód vyžadované vaší aplikaci chybí ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimka). Opravte tyto podmínky výjimek tak, že upravíte direktivy modulu runtime (. rd.xml) soubor zpřístupnit požadované metadata nebo provádění kódu za běhu. Další informace najdete v tématu [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Jsou k dispozici dva Poradce při potížích, zadejte odpovídající položky k nahrání souboru direktiv modulu runtime, který odstraní [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky:  
  
-   [Poradce při potížích MissingMetadataException](http://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
  
-   [Poradce při potížích MissingMetadataException](http://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
> [!NOTE]
>  Tento odkaz na dokumenty tři typy výjimek, které jsou jedinečné pro [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Referenční dokumentace pro rozhraní API reflexe .NET Framework core, najdete v části [obory názvů System.Reflection](https://msdn.microsoft.com/library/gg145033.aspx). Referenční dokumentace pro rozhraní API vzájemné spolupráce pro rozhraní .NET Framework core, najdete v části <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>Obor názvů System.Reflection  
 <xref:System.Reflection> Obor názvů obsahuje základní typy použité pro účely reflexe v rozhraní .NET Framework. Pro [!INCLUDE[net_native](../../../includes/net-native-md.md)], zahrnuje také dva nové typy výjimek:  
  
|Třída|Popis|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Výjimka, která je vyvolána při reflexi slouží k načtení metadat, která není k dispozici.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Výjimka, která je vyvolána, když je k dispozici metadat pro typ nebo člen typu, ale byla odebrána jeho implementace.|  
  
 Dokumentaci o ostatních typech v tomto oboru názvů, najdete v článku <xref:System.Reflection> odkazují na stránky v sadě dokumentace rozhraní .NET Framework.  
  
## <a name="systemruntimecompilerservices-namespace"></a>Obory názvů System.Runtime.CompilerServices  
 <xref:System.Runtime.CompilerServices> Obor názvů obsahuje typy určený pro uživatele pomocí kompilátorů jazyka. Pro [!INCLUDE[net_native](../../../includes/net-native-md.md)], také zahrnuje nový typ výjimky:  
  
|Třída|Popis|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Výjimka, která je vyvolána při zařazování metoda ruční nazývá, ale metadata pro typ nebyl nalezen ve statické analýzy nebo do souboru direktiv modulu runtime.|  
  
 Dokumentaci o ostatních typech v tomto oboru názvů, najdete v článku <xref:System.Runtime.CompilerServices> odkazují na stránky v sadě dokumentace rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 [Třída MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [Třída MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [Třída MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)
