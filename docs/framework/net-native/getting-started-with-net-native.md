---
title: "Začínáme s .NET Native"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
caps.latest.revision: "29"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eeda0c58e9b5e9f8b48e335849ce12f7e8d94a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started-with-net-native"></a>Začínáme s .NET Native
Ať už vytváříte nové aplikace pro Windows pro Windows 10 nebo migrujete stávající aplikace Windows Store, můžete postupovat podle stejnou sadu postupy. Chcete-li vytvořit [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikace, postupujte takto:  
  
1.  [Vývoj aplikace univerzální platformu Windows (UWP), která je cílena Windows 10](#Step1)a testovací ladění sestavení aplikace k zajištění, že bude správně fungovat.  
  
2.  [Zpracování další využití reflexe a serializace](#Step2).  
  
3.  [Nasaďte a otestujte verze sestavení aplikace](#Step3).  
  
4.  [Chybí metadata vyřešit ručně](#Step4)a opakujte [krok 3](#Step3) dokud všechny problémy nevyřeší.  
  
> [!NOTE]
>  Pokud provádíte migraci stávající aplikace Windows Store pro [!INCLUDE[net_native](../../../includes/net-native-md.md)], nezapomeňte si přečíst [migrace vaše aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
<a name="Step1"></a>   
## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>Krok 1: Vývoj a testovací ladicí sestavení aplikace UWP  
 Ať už jsou vývoj nové aplikace nebo migraci stávající, můžete postupujte stejně jako u libovolné aplikace pro Windows.  
  
1.  Vytvořte nový projekt UWP v sadě Visual Studio pomocí šablony aplikace Universal Windows pro Visual C# nebo Visual Basic. Ve výchozím nastavení všechny aplikace UWP cílit CoreCLR a jejich verzi sestavení jsou kompilovaná pomocí .NET Native nástroj řetězu.  
  
2.  Všimněte si, že jsou mezi kompilace projektů UPW aplikace .NET Native řetězem nástroj a bez některé problémy s kompatibilitou. Odkazovat [příručka k migraci](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md) Další informace.  
  
 Nyní můžete napsat kód C# nebo Visual Basic proti [!INCLUDE[net_native](../../../includes/net-native-md.md)] surface oblasti, která běží na lokálním systému (nebo v simulátoru).  
  
> [!IMPORTANT]
>  Když budete vyvíjet aplikace, Všimněte si jakékoli použití serializace nebo reflexe ve vašem kódu.  
  
 Ve výchozím nastavení, jsou sestavení pro ladění JIT zkompilovat umožňující rychlé nasazení F5, zatímco verzi sestavení jsou kompilovaná pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] předkompilaci technologie. To znamená, by měl sestavení a testů ladění sestavení aplikace k zajištění, že fungují normálně před jejich kompilace .NET Native řetězem nástroj.  
  
<a name="Step2"></a>   
## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>Krok 2: Zpracování serializace využití a další reflexe  
 Soubor direktivy modulu runtime Default.rd.xml, se automaticky přidá do projektu při jeho vytvoření. Pokud vyvíjíte v jazyce C#, zjistí ve vašem projektu **vlastnosti** složky. Pokud vyvíjíte v jazyce Visual Basic, zjistí ve vašem projektu **Můj projekt** složky.  
  
> [!NOTE]
>  Přehled procesu .NET Native kompilace, která poskytuje pozadí na důvod, proč je potřeba soubor direktivy modulu runtime, najdete v části [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Soubor direktivy modulu runtime se používá k definování metadata, která vaše aplikace, musí za běhu. V některých případech může stačit výchozí verzi souboru. Některé kód, který je založena na serializace a reflexe však může vyžadovat další záznamy v souboru direktivy modulu runtime.  
  
 **Serializace**  
 Existují dvě kategorie serializátorů a jak může vyžadovat další záznamy v souboru direktivy modulu runtime:  
  
-   Non-odrazových serializátorů. Serializátorů najít v knihovně tříd rozhraní .NET Framework, jako <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy, nespoléhejte na reflexi. Ale vyžadují generován kód založené na objekt, který má být serializován nebo deserializován.  Další informace najdete v části "Microsoft Serializers" v [serializace a Metadata](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
-   Serializátorů třetích stran. Knihovny serializace třetích stran, nejběžnější z nich je serializátor Newtonsoft JSON, jsou obvykle založené na reflexe a vyžadují položek v *. rd.xml soubor pro podporu objekt serializace a deserializace. Další informace najdete v části "Třetích stran Serializátorů" v [serializace a Metadata](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
 **Metody, které závisí na reflexi**  
 V některých případech není zřejmé použití reflexe v kódu. Některé společné rozhraní API nebo programovací vzory nejsou považovány za součást rozhraní API reflexe ale závisí na reflexi proběhl úspěšně. To zahrnuje následující vytvoření instance typu a metoda konstrukce metody:  
  
-   <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> – Metoda  
  
-   <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> a <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> metody  
  
-   <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Metoda.  
  
 Další informace najdete v tématu [rozhraní API, závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
> [!NOTE]
>  Názvy typů se používají v souborech direktivy modulu runtime musí být úplná. Například soubor musí zadat "System.String" místo "Řetězec".  
  
<a name="Step3"></a>   
## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>Krok 3: Nasaďte a otestujte verze sestavení vaší aplikace  
 Po aktualizaci soubor direktivy modulu runtime, můžete znovu vytvořit a nasadit sestavení verzi vaší aplikace. .NET native binární soubory jsou umístěny v adresáři zadaném v podadresáři ILC.out **sestavení výstupní cesta** textového pole projektu **vlastnosti** dialogové okno, **zkompilovat**kartě. Binární soubory, které nejsou v této složce nebyly kompilovaná pomocí .NET Native. Testování aplikace důkladně a otestovat všechny scénáře, včetně situací, selhání, na všech jeho cílové platformy.  
  
 Pokud vaše aplikace nebude fungovat správně (zejména v případech, kde vyvolá [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) nebo [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) výjimky za běhu), postupujte podle pokynů v dalším části [krok 4: vyřešit ručně chybí metadata](#Step4). Povolení první možnosti výjimky vám mohou pomoci najít tyto chyby.  
  
 Pokud byl testován a ladit ladění sestavení vaší aplikace a nejste jisti, že jste vyloučili [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) a [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) výjimky, měli byste otestovat aplikace jako optimalizované [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikace. K tomuto účelu změnit konfiguraci svého aktivní projekt z **ladění** k **verze**.  
  
<a name="Step4"></a>   
## <a name="step-4-manually-resolve-missing-metadata"></a>Krok 4: Vyřešit ručně chybí metadata  
 Nejběžnější selhání narazíte s [!INCLUDE[net_native](../../../includes/net-native-md.md)] nemáte narazíte na ploše je modul runtime [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), nebo [ MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimka. V některých případech chybí metadata může projevit v nepředvídatelné chování a dokonce i do selhání aplikace. Tato část popisuje, jak můžete ladění a tyto výjimky vyřešit přidáním direktivy k souboru direktivy modulu runtime. Informace o formátu direktivy modulu runtime najdete v tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Po přidání direktivy modulu runtime, měli byste [nasazení a testování aplikace](#Step3) znovu a vyřešte všechny nové [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, dokud narazíte na žádné další výjimky.  
  
> [!TIP]
>  Zadejte direktivy modulu runtime na vysoké úrovni chcete povolit aplikaci chcete být odolní vůči změny kódu.  Doporučujeme, abyste na úrovni oboru názvů a typ a nikoli na úrovni člena Přidání direktivy modulu runtime. Všimněte si, že může být kompromis mezi odolnost a větší binární soubory s delší doby kompilace.  
  
 Při adresování chybí metadata výjimky, zvažte tyto problémy:  
  
-   Co se aplikace snaží udělat před výjimka?  
  
    -   Například bylo datové vazby, serializaci nebo deserializaci dat nebo přímo pomocí reflexe rozhraní API?  
  
-   Je to izolované případu, nebo se domníváte, že budete dojde ke stejnému problému u jiných typů?  
  
    -   Například [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) při serializaci typu v modelu objektů aplikace je vyvolána výjimka.  Pokud znáte jiné typy, které budou serializovány, můžete přidat direktivy modulu runtime pro tyto typy (nebo pro jejich obsahující obory názvů, v závislosti na tom, jak dobře jsou uspořádána kód) ve stejnou dobu.  
  
-   Takže nepoužívá reflexe můžete přepsat kód?  
  
    -   Například používá kódu `dynamic` – klíčové slovo, když víte, jaké typy očekávat?  
  
    -   Kód volá metodu, která závisí na reflexi při některých lepší alternativou je k dispozici?  
  
> [!NOTE]
>  Další informace o zpracování problémy, které vyplývají z rozdíly v reflexe a dostupnost metadat v aplikacích klasické pracovní plochy a [!INCLUDE[net_native](../../../includes/net-native-md.md)], najdete v části [rozhraní API, která závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
 Některé konkrétní příklady zpracování výjimek a další problémy, ke kterým dochází při testování vaší aplikace najdete v části:  
  
-   [Příklad: Zpracování výjimek, pokud vazba dat](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)  
  
-   [Příklad: Řešení potíží s dynamické programování](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)  
  
-   [Výjimky za běhu v nativní aplikace .NET](../../../docs/framework/net-native/runtime-exceptions-in-net-native-apps.md)  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [NIB: .NET Native instalací a konfigurací](http://msdn.microsoft.com/en-us/7c9bc375-8b87-4c33-bede-72d513e362ec)  
 [.NET native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md)  
 [Reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Rozhraní API, která závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
 [Serializace a Metadata](../../../docs/framework/net-native/serialization-and-metadata.md)  
 [Migrace aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
