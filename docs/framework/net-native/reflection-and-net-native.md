---
title: Reflexe a .NET Native
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
ms.openlocfilehash: 65921377be9b8bf1c2d147b384c85cbd037d15f2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128189"
---
# <a name="reflection-and-net-native"></a>Reflexe a .NET Native
V .NET Framework podporuje spravovaný vývoj metaprogramování šablonou prostřednictvím rozhraní API pro reflexi. Reflexe umožňuje kontrolovat objekty v aplikaci, volat metody u objektů zjištěných prostřednictvím kontroly, generovat nové typy za běhu a podporuje mnoho dalších scénářů dynamického kódu. Podporuje také serializaci a deserializaci, která umožňuje trvalé a pozdější obnovení hodnot polí objektu. Tyto scénáře všechny vyžadují .NET Framework kompilátor JIT (just-in-time) pro generování nativního kódu na základě dostupných metadat.  
  
 Modul runtime .NET Native neobsahuje kompilátor JIT. V důsledku toho musí být všechny nezbytné nativní kódy vygenerovány předem. Sada heuristiky slouží k určení, jaký kód by měl být vygenerován, ale tyto heuristické metody nemůžou pokrývat všechny možné scénáře metaprogramování šablonou.  Proto je nutné poskytnout pomocný parametr pro tyto scénáře metaprogramování šablonou pomocí [direktiv modulu runtime](runtime-directives-rd-xml-configuration-file-reference.md). Pokud nejsou potřebná metadata nebo implementační kód k dispozici v době běhu, vaše aplikace vyvolá výjimku [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)nebo [MissingInteropDataException](missinginteropdataexception-class-net-native.md) . K dispozici jsou dva poradci při potížích, které budou generovat odpovídající položku pro váš soubor direktiv modulu runtime, který eliminuje výjimku:  
  
- [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
  
- Metody [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
> [!NOTE]
> Přehled procesu kompilace .NET Native, který poskytuje základní informace o tom, proč je soubor direktiv modulu runtime potřebný, naleznete v tématu [.NET Native a kompilace](net-native-and-compilation.md).  
  
 Kromě toho .NET Native neumožňuje odrážet soukromé členy knihovny tříd .NET Framework. Například volání <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> vlastnosti pro načtení polí typu knihovny třídy .NET Framework vrátí pouze veřejná nebo chráněná pole.  
  
 Následující témata popisují koncepční a referenční dokumentaci, kterou potřebujete pro podporu reflexe a serializace v aplikacích:  
  
- [Rozhraní API, která závisí na reflexi](apis-that-rely-on-reflection.md)  
  
- [Informace o rozhraní API reflexe](net-native-reflection-api-reference.md)  
  
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Viz také

- [Kompilování aplikací pomocí .NET Native](index.md)
- [.NET Native a kompilace](net-native-and-compilation.md)
