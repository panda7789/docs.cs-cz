---
title: Reflexe a .NET Native
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ba1c7056cfea3386e4456c09cc0c2ef98811053
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507223"
---
# <a name="reflection-and-net-native"></a>Reflexe a .NET Native
V rozhraní .NET Framework spravované podporuje vývoj metaprogramování prostřednictvím reflexe rozhraní API. Reflexe umožňuje kontrolu objektů v aplikaci, volání metod na objekty zjištěné prostřednictvím kontroly, generovat nové typy v době běhu a podporuje řadu dalších scénářů dynamický kód. Podporuje také serializace a deserializace, která umožňuje hodnoty pole objektu jako trvalý a později obnovit. Všechny tyto scénáře vyžadují kompilátor rozhraní .NET Framework just-in-time (JIT) ke generování nativního kódu na základě metadat k dispozici.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Runtime neobsahuje kompilátor JIT. V důsledku toho všechny nezbytné nativního kódu je nutné vygenerovat předem. Sadou heuristik slouží k určení, jaký kód by měl být vygenerován, ale tyto heuristiky pokrýt všechny možné metaprogramování scénáře.  Proto je nutné zadat pomocné parametry pro tyto scénáře metaprogramování pomocí [direktivy modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Pokud není k dispozici za běhu potřebná metadata nebo implementace kód, vaše aplikace vyvolá [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), nebo [ MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) výjimky. Jsou k dispozici dva Poradce při potížích, který vygeneruje na příslušnou položku k nahrání souboru direktiv modulu runtime, které předchází výjimku:  
  
-   [Poradce při potížích MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
  
-   [Poradce při potížích MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
> [!NOTE]
>  Získáte přehled o .NET Native proces kompilace, která poskytuje na pozadí na důvod, proč je potřeba soubor direktiv modulu runtime, naleznete v tématu [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Kromě toho [!INCLUDE[net_native](../../../includes/net-native-md.md)] neumožňuje reflexi pro soukromé členy v knihovně tříd rozhraní .NET Framework. Například volání <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> vlastnost k načtení pole rozhraní .NET Framework třída knihovny vrátí pouze veřejné nebo chráněné pole.  
  
 Následující témata poskytují koncepční a referenční dokumentaci, které potřebujete pro podporu reflexe a serializace ve vašich aplikacích:  
  
-   [Rozhraní API, která závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Informace o rozhraní API reflexe](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Viz také:
- [Kompilování aplikací pomocí .NET Native](../../../docs/framework/net-native/index.md)
- [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md)
