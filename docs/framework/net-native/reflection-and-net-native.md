---
title: Reflexe a .NET Native
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9e4bdc26815feab7910e7518f7cd691a1f4dece
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-and-net-native"></a>Reflexe a .NET Native
Ke správě podporuje vývoj metaprogramování prostřednictvím rozhraní API reflexe v rozhraní .NET Framework. Reflexe umožňuje zkontrolovat objekty v aplikaci, volat metody pro objekty zjištěné prostřednictvím kontroly, generování nových typů v době běhu a podporuje mnoho dalších scénářů dynamický kód. Podporuje také serializace a deserializace, což umožňuje objektu hodnoty polí jako trvalý, a později obnovit. Všechny tyto scénáře vyžadují rozhraní .NET Framework za běhu (JIT) kompilátor ke generování nativního kódu na základě metadat k dispozici.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Runtime neobsahuje kompilátoru za běhu. Všechny nezbytné nativního kódu v důsledku toho musí vygenerovat předem. Sadu heuristiky slouží k určení, jaký kód by měl být vygenerován, ale tyto heuristiky nelze zahrnují všechny možné metaprogramování scénáře.  Proto je nutné zadat pomocné parametry pro tyto scénáře metaprogramování s použitím [direktivy modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Pokud není k dispozici v době běhu nezbytné metadata nebo implementace kód, vyvolá vaší aplikace [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), nebo [ MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) výjimka. Jsou k dispozici dva Poradce při potížích, vygeneruje na příslušnou položku pro váš soubor direktivy modulu runtime, který eliminuje výjimka:  
  
-   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
  
-   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
> [!NOTE]
>  Přehled procesu .NET Native kompilace, která poskytuje pozadí na důvod, proč je potřeba soubor direktivy modulu runtime, najdete v části [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Kromě toho [!INCLUDE[net_native](../../../includes/net-native-md.md)] neumožňuje, aby odrážela přes soukromé členy knihovně tříd rozhraní .NET Framework. Například volání <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> vlastnost k načtení pole rozhraní .NET Framework – třída knihovny typu vrátí pouze veřejné nebo chráněného polí.  
  
 Následující témata poskytují koncepční a referenční dokumentace, která budete potřebovat k podpoře reflexe a serializace ve svých aplikacích:  
  
-   [Rozhraní API, která závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Referenční dokumentace rozhraní API reflexe](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Viz také  
 [Kompilování aplikací pomocí .NET Native](../../../docs/framework/net-native/index.md)  
 [.NET native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md)
