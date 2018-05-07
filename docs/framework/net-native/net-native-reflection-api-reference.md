---
title: Informace o rozhraní API reflexe .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ea47b8402f1bd2f66c957ff9126c8dff094a7ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="net-native-reflection-api-reference"></a>Informace o rozhraní API reflexe .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] zahrnuje tři nové typy výjimek: [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), a [ System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Vezměte na vědomí následující skutečnosti související všechny typy tři výjimka:  
  
 Tyto typy jsou pouze pro interní použití.  
 Tyto tři výjimka typy jsou pro použití [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj pouze řetězce. Výjimky jsou vyvolány, když [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu zjistí chybějící data, který neumožňuje spuštění programu pokračujte.  
  
 Nezpracuje tyto výjimky v kódu.  
 Tyto výjimky znamenat chybí buď aby metadata vyžaduje vaše aplikace ( [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky) nebo že implementace kódu vyžaduje vaše aplikace nebyl nalezen ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimka). Opravte tyto podmínky výjimka změnou direktivy modulu runtime (. rd.xml) soubor zpřístupnit požadovaná metadata nebo implementaci kódu v době běhu. Další informace najdete v tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Jsou k dispozici dva Poradce při potížích, zadejte odpovídající položky pro váš soubor direktivy modulu runtime, který bude eliminovat [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky:  
  
-   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
  
-   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
> [!NOTE]
>  Tento odkaz dokumenty tři typy výjimek, které jsou jedinečné pro [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Referenční dokumentace pro rozhraní .NET Framework odraz jádra rozhraní API, najdete v části [obory názvů System.Reflection](http://msdn.microsoft.com/library/gg145033.aspx). Referenční dokumentace rozhraní API spolupráce pro rozhraní .NET Framework core, najdete v části <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>Obor názvů System.Reflection  
 <xref:System.Reflection> Obor názvů obsahuje typy základní používané pro reflexe v rozhraní .NET Framework. Pro [!INCLUDE[net_native](../../../includes/net-native-md.md)], zahrnuje také dva nové typy výjimka:  
  
|Třída|Popis|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Výjimka, která se vyvolá, když reflexe se používá k načtení metadat, která není přítomen.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Výjimka, která se vyvolá, když je k dispozici metadata pro typ nebo člen typu, ale jeho implementace byl odebrán.|  
  
 Dokumentaci k jiné typy v tomto oboru názvů, najdete <xref:System.Reflection> odkazovat stránek v dokumentaci k sadě rozhraní .NET Framework.  
  
## <a name="systemruntimecompilerservices-namespace"></a>Obory názvů System.Runtime.CompilerServices  
 <xref:System.Runtime.CompilerServices> Obor názvů obsahuje typy, které jsou určené pro uživatele pomocí kompilátory jazyka. Pro [!INCLUDE[net_native](../../../includes/net-native-md.md)], zahrnuje také nový typ výjimky:  
  
|Třída|Popis|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Výjimka, která se vyvolá, když ruční zařazování metoda je volána, ale metadata pro typ nebyl nalezen statické analýzou nebo v souboru direktivy modulu runtime.|  
  
 Dokumentaci k jiné typy v tomto oboru názvů, najdete <xref:System.Runtime.CompilerServices> odkazovat stránek v dokumentaci k sadě rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 [Třída MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [Třída MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [Třída MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)
