---
title: Obecné řešení potíží s .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81ff8a347235ab1a765b4f41051dab2da786b89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866869"
---
# <a name="net-native-general-troubleshooting"></a>Obecné řešení potíží s .NET Native
Toto téma popisuje postupy řešení potíží s potenciální problémy, které se mohou vyskytnout při vývoji aplikací s využitím [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
- **Problém:** Okno výstup sestavení není správně aktualizovat.  
  
     **Řešení:** V okně výstupu sestavení není aktualizován, dokud se nedokončí sestavení. Dobu sestavení může být až několik minut, proto může docházet ke zpoždění v zobrazení aktualizací.  
  
- **Problém:** Čas sestavení prodejní vaší aplikace pro ARM zvýšil.  
  
     **Řešení:** Při nasazení aplikace do zařízení ARM, [!INCLUDE[net_native](../../../includes/net-native-md.md)] infrastruktury je vyvolána. Tato kompilace provádí velké množství optimalizace při zajištění tuto sémantiku nestatické, jako je odraz pokračovat v práci. Kromě toho část aplikace využívá rozhraní .NET Framework je staticky propojena k zajištění optimálního výkonu a musí být kompilovány do nativního kódu i. To je důvod, proč kompilace trvá déle.  
  
     Časy kompilace jsou však stále během minuty standardní kompilace pro většinu aplikací na standardní vývojovém počítači.  Právě generování nativních bitových kopií pro rozhraní .NET Framework v počítači vývoje ve standardu obvykle trvá několik minut.  I přes všechny optimalizace pro zlepšení generovaného kódu a pomocí rozhraní .NET Framework včetně doby sestavení aplikace jsou obvykle minutu nebo dvě.  
  
     Pokračujeme v práci na zlepšení výkonu kompilace zjišťováním vícevláknovou kompilaci a další optimalizace.  
  
- **Problém:** Nevíte, pokud vaše aplikace byla sestavena pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
     **Řešení:** Pokud [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler je vyvolán, můžete si všimnout delší doby sestavení a Správce úloh se zobrazí různé [!INCLUDE[net_native](../../../includes/net-native-md.md)] komponenty procesy, jako je například ILC.exe a nutc_driver.exe.  
  
     Po úspěšném sestavení svého projektu pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)], najdete ve výstupu pod obj\\*config*\ *arch* \\  *ProjectName*. ilc\out.  Nativní finálním balíčku obsahu najdete v části bin\\*arch*\\*config*\AppX. Nativní finálním balíčku obsahu jsou v rámci \bin\\*arch*\\*config*\AppX Pokud jste nasadili aplikaci.  
  
- **Problém:** .NET Native kompilací aplikace vyvolává výjimky modulu CLR (obvykle [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) nebo [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky), že ho nevyvolala při zkompilovány bez volby. NET nativní.  
  
     **Řešení:** Výjimky jsou vyvolány, protože .NET Native neposkytl metadata nebo implementační kód, který je jinak k dispozici prostřednictvím reflexe. (Další informace najdete v tématu [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).) Chcete-li odstranit výjimky, budete muset přidat položku pro váš [soubor modulu runtime (rd.xml) direktivy](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) tak, aby .NET Native řetězce nástrojů můžete zpřístupnit metadata nebo provádění kódu za běhu. Jsou k dispozici dva Poradce při potížích, která bude generovat nezbytné položku a přidejte do souboru direktiv modulu runtime:  
  
    - [Poradce při potížích MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.  
  
    - [Poradce při potížích MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) pro metody.  
  
     Další informace najdete v tématu [reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).  
  
## <a name="see-also"></a>Viz také:

- [Migrace aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
