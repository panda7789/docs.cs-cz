---
title: "Obecné řešení potíží s .NET Native"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e92e99b978d12c32cc46b9133621875f35af634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="net-native-general-troubleshooting"></a>Obecné řešení potíží s .NET Native
Toto téma popisuje postupy řešení potíží s potenciálními problémy, které se můžete setkat při vývoji aplikací s [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   **Problém:** okně výstupu sestavení, správně neaktualizuje.  
  
     **Řešení:** ve výstupním okně sestavení není aktualizován, dokud se nedokončí sestavení. Sestavení může trvat až několik minut, proto může docházet ke zpoždění v zobrazení aktualizací.  
  
-   **Problém:** prodejní vaší aplikace pro ARM zvýšilo čas sestavení.  
  
     **Řešení:** při nasazení aplikace do zařízení ARM [!INCLUDE[net_native](../../../includes/net-native-md.md)] infrastruktury je volána. Tato kompilace provede velký počet optimalizace a zajistit, že sémantika nestatické například reflexe pokračovat v práci. Kromě toho část rozhraní .NET Framework, který používá aplikace je staticky propojené v pro optimální výkon a musí být zkompilovány do nativního kódu také. Z tohoto důvodu kompilace trvá déle.  
  
     Dobu kompilace jsou však stále do jedné minuty standardní kompilace pro většinu aplikací na standardní vývojovém počítači.  Právě generování nativních bitových kopií pro rozhraní .NET Framework na standardní vývojovém počítači obvykle trvá několik minut.  I s všechny optimalizace k vylepšení generovaného kódu a včetně rozhraní .NET Framework časy sestavení aplikace jsou obvykle minutu nebo dvě.  
  
     Jsme nadále fungovat na zvýšení výkonu kompilace zjišťováním kompilace vícevláknových a další optimalizace.  
  
-   **Problém:** nevíte, pokud vaše aplikace byl kompilován s použitím [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
     **Řešení:** Pokud [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilátoru je volána, můžete si všimnout již sestavení časy a Správce úloh se zobrazí různé [!INCLUDE[net_native](../../../includes/net-native-md.md)] součást procesy, například ILC.exe a nutc_driver.exe.  
  
     Po úspěšném sestavení projektu s [!INCLUDE[net_native](../../../includes/net-native-md.md)], zjistíte výstup pod obj\\*konfigurace*\ *architektura* \\  *název projektu*. ilc\out.  Poslední nativní balíčku obsahu najdete v části bin\\*architektura*\\*konfigurace*\AppX. Obsah konečné nativní balíčku se v části \bin\\*architektura*\\*konfigurace*\AppX Pokud jste nasadili aplikace.  
  
-   **Problém:** aplikace .NET Native zkompilovat je vyvolání výjimky za běhu (obvykle [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) nebo [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky), jeho nebyla výjimku při kompilovat bez .NET Native.  
  
     **Řešení:** výjimky jsou vyvolány, protože .NET Native neposkytl metadata nebo implementace kód, který je jinak k dispozici prostřednictvím reflexe. (Další informace najdete v tématu [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).) Odstranit výjimku, budete muset přidat položku s vaší [runtime (rd.xml) direktivy souboru](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) tak, aby řetězu .NET Native nástroj můžete zpřístupnit metadata nebo implementaci kódu v době běhu. Jsou k dispozici dva Poradce při potížích, bude generovat potřeby položku pro přidání do souboru direktivy modulu runtime:  
  
    -   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
  
    -   [MissingMetadataException Poradce při potížích s](http://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
     Další informace najdete v tématu [reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).  
  
## <a name="see-also"></a>Viz také  
 [Migrace aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
