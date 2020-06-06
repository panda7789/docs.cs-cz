---
title: Informace o rozhraní API reflexe .NET Native
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
ms.openlocfilehash: 01678ea6230a53416f213730ae6bb66e6bc057f8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128221"
---
# <a name="net-native-reflection-api-reference"></a>Informace o rozhraní API reflexe .NET Native
.NET Native obsahuje tři nové typy výjimek: [System. Runtime. CompilerServices. MissingInteropDataException](missinginteropdataexception-class-net-native.md), [System. Reflection. MissingMetadataException](missingmetadataexception-class-net-native.md)a [System. Reflection. MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md). Všimněte si následujících informací o všech třech typech výjimek:  
  
 Tyto typy jsou pouze pro interní použití.  
 Tyto tři typy výjimek jsou pouze pro použití řetězu nástroje .NET Native. Výjimky jsou vyvolány, když řetěz nástrojů .NET Native detekuje chybějící data, která neumožňují spuštění programu pokračovat.  
  
 Tyto výjimky v kódu nezpracujte.  
 Tyto výjimky signalizují, že metadata potřebná vaší aplikací nejsou k dispozici (výjimky [MissingInteropDataException](missinginteropdataexception-class-net-native.md) a [MissingMetadataException](missingmetadataexception-class-net-native.md) ) nebo že kód implementace vyžadovaný vaší aplikací chybí (výjimka [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) ). Tyto podmínky výjimky opravíte úpravou souboru direktiv modulu runtime (. Rd. XML), aby byla požadovaná metadata nebo implementační kód k dispozici za běhu. Další informace najdete v tématu [Referenční dokumentace ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md). K dispozici jsou dva poradci při potížích, které poskytují vhodné položky pro soubor direktiv runtime, který eliminuje výjimky [MissingMetadataException](missingmetadataexception-class-net-native.md) a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) :  
  
- [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
  
- Metody [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
> [!NOTE]
> Tento odkaz odkazuje na tři typy výjimek, které jsou jedinečné pro .NET Native. Referenční dokumentaci pro rozhraní API pro základní reflexi .NET Framework naleznete v tématu <xref:System.Reflection> <xref:System.Reflection.Context> a v <xref:System.Reflection.Emit> oborech názvů. Referenční dokumentaci k rozhraní API pro interoperabilitu .NET Framework Core najdete v tématu <xref:System.Runtime.InteropServices> .  
  
## <a name="systemreflection-namespace"></a>Obor názvů System. Reflection  
 <xref:System.Reflection>Obor názvů obsahuje základní typy používané pro reflexi v .NET Framework. Pro .NET Native obsahuje také dva nové typy výjimek:  
  
|Třída|Description|  
|-----------|-----------------|  
|[MissingMetadataException](missingmetadataexception-class-net-native.md)|Výjimka, která je vyvolána, když je použita reflexe k načtení metadat, která nejsou k dispozici.|  
|[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)|Výjimka, která je vyvolána, když jsou k dispozici metadata pro typ nebo člen typu, ale jeho implementace byla odebrána.|  
  
 Dokumentaci k ostatním typům v tomto oboru názvů najdete v tématu <xref:System.Reflection> referenční stránky v sadě .NET Framework dokumentace.  
  
## <a name="systemruntimecompilerservices-namespace"></a>Obor názvů System. Runtime. CompilerServices  
 <xref:System.Runtime.CompilerServices>Obor názvů obsahuje typy určené pro uživatele v kompilátorech jazyka. Pro .NET Native obsahuje také nový typ výjimky:  
  
|Třída|Description|  
|-----------|-----------------|  
|[MissingInteropDataException](missinginteropdataexception-class-net-native.md)|Výjimka, která je vyvolána při volání metody ručního zařazování, ale metadata pro typ nejsou nalezena statickou analýzou nebo v souboru direktiv modulu runtime.|  
  
 Dokumentaci k ostatním typům v tomto oboru názvů najdete v tématu <xref:System.Runtime.CompilerServices> referenční stránky v sadě .NET Framework dokumentace.  
  
## <a name="see-also"></a>Viz také

- [Třída MissingInteropDataException](missinginteropdataexception-class-net-native.md)
- [Třída MissingMetadataException](missingmetadataexception-class-net-native.md)
- [Třída MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)
- [Začínáme](getting-started-with-net-native.md)
