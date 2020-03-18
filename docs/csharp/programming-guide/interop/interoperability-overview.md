---
title: Přehled interoperability – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 2c9eb2a8e6c2db8dc06ebe48ca6eb37d5cf638e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700728"
---
# <a name="interoperability-overview-c-programming-guide"></a>Přehled interoperability (Průvodce programováním v C#)
Téma popisuje metody, které umožňují interoperabilitu mezi spravovaným kódem jazyka C# a nespravovaným kódem.  
  
## <a name="platform-invoke"></a>Vyvolání platformy  
 *Vyvolání platformy* je služba, která umožňuje spravovanému kódu volat nespravované funkce, které jsou implementovány v knihovnách dll dynamických odkazů (DLL), jako jsou ty v rozhraní MICROSOFT Windows API. Vyhledá a vyvolá exportovanou funkci a zařazuje její argumenty (celá čísla, řetězce, pole, struktury a tak dále) přes hranice vzájemné spolupráce podle potřeby.  
  
Další informace naleznete [v tématech Náročné nespravované funkce dll](../../../framework/interop/consuming-unmanaged-dll-functions.md) a [Jak použít vyvolání platformy k přehrání souboru WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md).
  
> [!NOTE]
> [Clr (Common Language Runtime)](../../../standard/clr.md) spravuje přístup k systémovým prostředkům. Volání nespravovaného kódu, který je mimo CLR obchází tento mechanismus zabezpečení a proto představuje bezpečnostní riziko. Nespravovaný kód může například volat prostředky v nespravovaném kódu přímo, čímž obchází mechanismy zabezpečení CLR. Další informace naleznete [v tématu Zabezpečení v rozhraní .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>interoperabilita C++  
 Můžete použít C++ interop, také známý jako to jen funguje (IJW), zabalit nativní C++ třídy tak, aby mohly být spotřebovány kód, který je vytvořen v jazyce C# nebo jiný jazyk rozhraní .NET Framework. Chcete-li to provést, napište kód C++ pro zabalení nativní dll nebo com komponenty. Na rozdíl od jiných jazyků rozhraní .NET Framework má visual c++ podporu interoperability, která umožňuje umístění spravovaného a nespravovaného kódu ve stejné aplikaci a dokonce i ve stejném souboru. Potom sestavit kód Jazyka C++ pomocí přepínače kompilátoru **/clr** k vytvoření spravovaného sestavení. Nakonec přidáte odkaz na sestavení v projektu Jazyka C# a použít zabalené objekty stejně jako byste použít jiné spravované třídy.  
  
## <a name="exposing-com-components-to-c"></a>Vystavení komponent com c\#
 Komponentu MODELU COM můžete spotřebovat z projektu jazyka C#. Obecné kroky jsou následující:  
  
1. Vyhledejte komponentu modelu COM, která ji chcete použít, a zaregistrujte ji. Pomocí příkazu regsvr32.exe zaregistrujte nebo zrušte registraci dll com.  
  
2. Přidejte do projektu odkaz na komponentu nebo knihovnu typů modelu COM.  
  
     Když přidáte odkaz, Visual Studio používá [Tlbimp.exe (Typ knihovny Import)](../../../framework/tools/tlbimp-exe-type-library-importer.md), který trvá knihovnu typů jako vstup, k výstupu .NET Framework interop sestavení. Sestavení s názvem runtime callable wrapper (RCW) obsahuje spravované třídy a rozhraní, které obtékat třídy COM a rozhraní, které jsou v knihovně typů. Visual Studio přidá do projektu odkaz na generované sestavení.  
  
3. Vytvořte instanci třídy, která je definována v RCW. To zase vytvoří instanci objektu COM.  
  
4. Objekt používejte stejně jako jiné spravované objekty. Když je objekt uvolněn uvolněním paměti, instance objektu COM je také uvolněna z paměti.  
  
 Další informace naleznete v [tématu Vystavení komponent komuzitu rozhraní .NET Framework](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Vystavení c# com  
 Klienti COM mohou využívat typy Jazyka C#, které byly správně vystaveny. Základní kroky k vystavení c# typy jsou následující:  
  
1. Přidejte atributy interop v projektu C#.  
  
     Com sestavení můžete zviditelnit úpravou vlastností projektu Visual C#. Další informace naleznete v [tématu Dialog informace o sestavě](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Vygenerujte knihovnu typů com a zaregistrujte ji pro použití com.  
  
     Můžete upravit vlastnosti projektu Visual C# a automaticky zaregistrovat sestavení C# pro interop COM. Visual Studio používá [Regasm.exe (Nástroj pro registraci sestavení)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)pomocí přepínače `/tlb` příkazového řádku, který přebírá spravované sestavení jako vstup, ke generování knihovny typů. Tato knihovna typů `public` popisuje typy v sestavení a přidává položky registru, aby klienti COM mohli vytvářet spravované třídy.  
  
 Další informace naleznete [v tématu Vystavení součástí rozhraní .NET Framework pro com](../../../framework/interop/exposing-dotnet-components-to-com.md) a příklad [třídy COM](./example-com-class.md).  
  
## <a name="see-also"></a>Viz také

- [Zlepšení výkonu interop](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [Úvod do interoperability mezi com a .NET](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Úvod do kominterop v jazyce Visual Basic](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Zařazování mezi spravovaným a nespravovaným kódem](../../../framework/interop/interop-marshaling.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Programovací příručka jazyka C#](../index.md)
