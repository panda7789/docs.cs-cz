---
title: Koncepty serializace
ms.date: 08/07/2017
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
ms.openlocfilehash: 1a7fa7c3e5561fc9e48cf627a703abc747a72ba0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159829"
---
# <a name="serialization-concepts"></a>Koncepty serializace
Proč byste se měli použít serializaci? Dva nejdůležitější důvody jsou k uchování stav objektu do úložiště média, takže přesná kopie může být později znovu vytvořena a posílat objektu podle hodnoty od jeden aplikační domény do druhé. Můžete například serializace slouží k uložení stavu relace technologie ASP.NET a objekty zkopírovat do schránky ve Windows Forms. Také se používá ve vzdálené komunikace předat objekty podle hodnoty z domény jednu aplikaci do jiného.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Trvalé úložiště
Často je nezbytné k uložení hodnoty polí objektu na disk a potom později načíst tato data. Přestože je to snadné dosáhnout bez ohledu na serializace, tento přístup je často náročný a chyby k chybám a změní postupně složitější, pokud je třeba sledovat hierarchie objektů. Představte si aplikaci velké firmy, která obsahuje tisíce objekty, zápisu a nutnosti psaní kódu pro uložení a obnovení polí a vlastností, z disku a disk pro každý objekt. Serializace poskytuje vhodný mechanismus pro dosažení tohoto cíle.

Modul CLR (Common Language Runtime) spravuje, jak jsou objekty uloženy v paměti a poskytuje mechanismus automatizované serializace pomocí [reflexe](../../../docs/framework/reflection-and-codedom/reflection.md). Pokud je objekt serializován, název třídy, sestavení a datových členů instance třídy jsou zapsány do úložiště. Objekty často ukládat odkazy na další instance proměnné členů. Při serializován třídu pro Serializační stroj sleduje odkazované objekty, již serializován, chcete-li zajistit, že na stejný objekt nelze serializovat, více než jednou. Architektura serializace dodaná s .NET Framework správně zpracovává grafy objektů a cyklické odkazy automaticky. Jediným požadavkem umístěným v grafech objektů je, že všechny objekty, na které je odkazován serializovaným objektem `Serializable` , musí být také označeny jako (Další informace naleznete v tématu [Základní serializace](basic-serialization.md)). Pokud není to, bude vyvolána výjimka, když serializátor pokusí serializaci zrušeno označení objektu.

Při deserializaci serializované třídy se třída znovu vytvoří a hodnoty všech datových členů se obnoví automaticky.

## <a name="marshal-by-value"></a>Zařazení podle hodnoty
Objekty jsou platné pouze v doméně aplikace, kde jsou vytvořeny. Jakýkoliv pokus o předání objektu jako parametru nebo jeho vrácení jako výsledek selže, pokud objekt není odvozen z `MarshalByRefObject` nebo je označen jako. `Serializable` Pokud je objekt označen jako `Serializable`, objekt bude automaticky serializován, přepravován z jedné aplikační domény do druhé a poté deserializovat, aby vytvořila přesnou kopii objektu v druhé aplikační doméně. Tento proces je obvykle označován jako zařazování podle hodnot.

Pokud je objekt odvozen z `MarshalByRefObject`, odkaz na objekt je předán z jedné aplikační domény do druhé, nikoli samotného objektu. Můžete také označit objekt, který je odvozen z `MarshalByRefObject` as. `Serializable` Pokud je tento objekt použit se vzdáleným přístupem, formátovací modul zodpovědný za serializaci, který byl předem nakonfigurován pomocí náhradního selektor`SurrogateSelector`(), přebírá kontrolu nad procesem serializace a nahrazuje všechny objekty odvozené `MarshalByRefObject` z s proxy serverem. `SurrogateSelector` Bez toho, architektura serializace dodržuje standardní pravidla serializace popsaná v [krocích procesu serializace](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>Související oddíly  
 [Binární serializace](../../../docs/standard/serialization/binary-serialization.md)  
 Popisuje binární serializace mechanismus, který je součástí common language runtime.  
  
 [Vzdálená komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
 Popisuje různé komunikační metody k dispozici v rozhraní .NET Framework pro vzdálenou komunikaci.  
  
 [Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Popisuje mechanismus serializace XML a SOAP, která je součástí common language runtime.
