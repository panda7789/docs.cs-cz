---
title: Přehled interoperability – Průvodce programováním v C#
description: Seznamte se s interoperabilitou mezi C# a nespravovaným kódem, včetně vyvolání platforem, interoperability C++, vystavení komponent COM v jazyce C# a vystavení C# modelu COM.
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 6b1dec96dfb3fc354c614983ed1dafab66c5b007
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302955"
---
# <a name="interoperability-overview-c-programming-guide"></a>Přehled interoperability (Průvodce programováním v C#)
Téma popisuje metody pro povolení interoperability mezi spravovaným kódem C# a nespravovaným kódem.  
  
## <a name="platform-invoke"></a>Vyvolání platformy  
 *Vyvolání platformy* je služba, která umožňuje spravovanému kódu volat nespravované funkce, které jsou implementované v knihovně DLL (Dynamic Link Library), například v rozhraní Microsoft Windows API. Vyhledá a vyvolá exportovanou funkci a zařadí argumenty (celá čísla, řetězce, pole, struktury atd.) v rámci hranice mezioperace podle potřeby.  
  
Další informace naleznete v tématu [spotřebovávání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) a [použití vyvolání platformy k přehrání souboru WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md).
  
> [!NOTE]
> Modul CLR ( [Common Language Runtime](../../../standard/clr.md) ) spravuje přístup k systémovým prostředkům. Volání nespravovaného kódu, který je mimo CLR, obchází tento mechanismus zabezpečení a proto představuje bezpečnostní riziko. Nespravovaný kód například může volat prostředky v nespravovaném kódu přímo, obejít mechanismy zabezpečení CLR. Další informace najdete v tématu [zabezpečení v .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>interoperabilita C++  
 Můžete použít interoperabilitu C++, označovanou také jako pouze funguje (IJW), k zabalení nativní třídy jazyka C++ tak, aby ji bylo možné spotřebovat kódem, který je vytvořen v jazyce C# nebo v jiném jazyce .NET. Chcete-li to provést, napíšete kód jazyka C++ pro zabalení nativní knihovny DLL nebo komponenty modelu COM. Na rozdíl od jiných jazyků .NET Visual C++ má podporu interoperability, která umožňuje umístění spravovaného a nespravovaného kódu ve stejné aplikaci a dokonce i ve stejném souboru. Potom sestavíte kód jazyka C++ pomocí přepínače **/CLR** pro vytvoření spravovaného sestavení. Nakonec přidáte odkaz na sestavení v projektu C# a použijete zabalené objekty stejně, jako byste používali jiné spravované třídy.  
  
## <a name="exposing-com-components-to-c"></a>Vystavení komponent modelu COM v jazyce C\#
 Komponentu modelu COM můžete využívat z projektu C#. Obecné kroky jsou následující:  
  
1. Vyhledejte komponentu modelu COM, kterou chcete použít, a zaregistrujte ji. Použijte regsvr32.exe k registraci nebo zrušení registrace knihovny COM.  
  
2. Přidejte do projektu odkaz na komponentu COM nebo knihovny typů.  
  
     Když přidáte odkaz, aplikace Visual Studio používá [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md), který jako vstup převezme knihovnu typů, aby mohl výstup sestavení Interop .NET. Sestavení, také pojmenované obálka RCW (Runtime), obsahuje spravované třídy a rozhraní, která zabalí třídy modelu COM a rozhraní, která jsou v knihovně typů. Visual Studio přidá do projektu odkaz na vygenerované sestavení.  
  
3. Vytvořte instanci třídy, která je definována v RCW. To zase vytvoří instanci objektu COM.  
  
4. Použijte objekt stejně jako ostatní spravované objekty. Když je objekt uvolněn uvolňováním paměti, instance objektu COM je také uvolněna z paměti.  
  
 Další informace najdete v tématu vystavení [komponent COM na .NET Framework](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Vystavení C# pro COM  
 Klienti modelu COM mohou využívat typy C#, které byly správně zpřístupněny. V základních krocích k vystavování typů C# jsou tyto:  
  
1. Přidejte atributy spolupráce v projektu C#.  
  
     Model COM sestavení lze zviditelnit úpravou vlastností projektu jazyka Visual C#. Další informace najdete v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Vygenerujte knihovnu typů modelu COM a zaregistrujte ji pro použití v modelu COM.  
  
     Můžete upravit vlastnosti projektu Visual C# a automaticky registrovat sestavení v jazyce C# pro zprostředkovatele komunikace s objekty COM. Visual Studio používá [Regasm.exe (Nástroj pro registraci sestavení)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)pomocí `/tlb` přepínače příkazového řádku, který přebírá spravované sestavení jako vstup pro vygenerování knihovny typů. Tato knihovna typů popisuje `public` typy v sestavení a přidává položky registru, aby klienti modelu COM mohli vytvořit spravované třídy.  
  
 Další informace najdete v tématu vystavení [.NET Framework komponent do modelu COM](../../../framework/interop/exposing-dotnet-components-to-com.md) a [Ukázkové třídy com](./example-com-class.md).  
  
## <a name="see-also"></a>Viz také:

- [Zlepšení výkonu spolupráce](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [Seznámení s interoperabilitou mezi COM a .NET](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Seznámení se zprostředkovatelem komunikace s objekty COM v Visual Basic](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Zařazování mezi spravovaným a nespravovaným kódem](../../../framework/interop/interop-marshaling.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Průvodce programováním v C#](../index.md)
