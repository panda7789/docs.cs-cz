---
title: Obecné řešení potíží s .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5f61b0e250c4f51a966bc60959f7559d8e2fe2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049404"
---
# <a name="net-native-general-troubleshooting"></a>Obecné řešení potíží s .NET Native

Toto téma popisuje, jak řešit potenciální problémy, se kterými se můžete setkat při vývoji aplikací pomocí .NET Native.

- **Chybu** Okno výstup sestavení není správně aktualizováno.

  **Řešení:** Okno výstup sestavení není aktualizováno, dokud sestavení není dokončeno. Doba sestavování může trvat až několik minut, takže se můžete setkat se zpožděním v zobrazení aktualizací.

- **Chybu** Čas maloobchodního sestavení vaší aplikace pro ARM se zvýšil.

  **Řešení:** Když nasadíte aplikaci do zařízení ARM, vyvolá se .NET Native infrastruktura. Tato kompilace provádí velký počet optimalizací a zároveň zajišťuje, aby nestatická sémantika, jako je například reflexe, pokračovala v práci. Kromě toho část .NET Framework, kterou aplikace používá, je staticky propojena v pro zajištění optimálního výkonu a musí být zkompilována také do nativního kódu. To je důvod, proč kompilace trvá déle.

  Doby kompilace jsou však stále v průběhu jedné minuty standardní kompilace pro většinu aplikací na standardním vývojovém počítači.  Obvykle pouze generování nativních imagí pro .NET Framework na standardním vývojovém počítači trvá několik minut.  I se všemi optimalizacemi pro zlepšení vygenerovaného kódu a zahrnutím .NET Framework jsou časy sestavení aplikací obvykle minuty nebo dva.

  Pokračujeme v práci na vylepšení výkonu kompilace zkoumáním vícevláknové kompilace a dalších optimalizací.

- **Chybu** Nevíte, zda byla aplikace kompilována pomocí .NET Native.

  **Řešení:** Pokud je vyvolán kompilátor .NET Native, všimnete si delší doby sestavení a Správce úloh bude zobrazovat různé procesy .NET Native komponent, jako je ILC. exe a nutc_driver. exe.

  Po úspěšném sestavení projektu s .NET Native najdete\\výstup v části\\obj*Konfigurace souboru*\ *ProjectName*. ilc\out.  Konečný obsah nativního balíčku najdete v části\\bin*arch*\\*config*\AppX. Konečný obsah nativního balíčku najdete v části\\ *\Bin*\\\AppX*config*, pokud jste nasadili aplikaci.

- **Chybu** Vaše .NET Native kompilovaná aplikace vyvolává výjimky za běhu (obvykle [MissingMetadataException](missingmetadataexception-class-net-native.md) nebo [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) ), které nebyly vyvolávat při kompilaci bez .NET Native.

  **Řešení:** Výjimky jsou vyvolány, protože .NET Native neposkytoval buď metadata, nebo implementační kód, který je jinak dostupný prostřednictvím reflexe. (Další informace najdete v tématu [.NET Native a kompilace](net-native-and-compilation.md)). Chcete-li výjimku eliminovat, je nutné přidat položku do [souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md) , aby řetěz nástrojů .NET Native mohl zpřístupnit metadata nebo implementační kód za běhu. K dispozici jsou dva Poradce při potížích, které vygenerují nezbytnou položku pro přidání do souboru direktiv modulu runtime:

  - [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) pro typy.

  - Metody [Poradce při potížích s MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .

  Další informace naleznete v tématu [reflexe and .NET Native](reflection-and-net-native.md).

## <a name="see-also"></a>Viz také:

- [Migrace aplikace pro Windows Store do .NET Native](migrating-your-windows-store-app-to-net-native.md)
