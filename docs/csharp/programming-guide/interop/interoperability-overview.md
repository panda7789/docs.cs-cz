---
title: "Přehled interoperability (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7e4bc1814ed5c86660b4333542a3dc4eb7462e89
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="interoperability-overview-c-programming-guide"></a>Přehled interoperability (Průvodce programováním v C#)
Téma popisuje metody a umožňuje interoperabilitu mezi C# spravovaný kód a nespravovaného kódu.  
  
## <a name="platform-invoke"></a>Vyvolání platformy  
 *Vyvolání platformy* je služba, což umožňuje spravovat kódu volání nespravovaných funkcí, které jsou implementované v dynamické knihovny (DLL), například v rozhraní API Win32 společnosti Microsoft. Vyhledá a vyvolá exportované funkce a zařazuje její argumenty (celá čísla, řetězce, pole, struktur a tak dále) přes součinnosti hranice, podle potřeby.  
  
 Další informace najdete v tématu [využívání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) a [postupy: použití vyvolání platformy pro přehrání souboru Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Modul Common Language Runtime](../../../standard/clr.md) (CLR) spravuje přístup k systémovým prostředkům. Volání nespravovaného kódu, který je mimo modulu CLR obchází tento mechanismus zabezpečení a proto představuje bezpečnostní riziko. Nespravovaný kód může například volání prostředky v nespravovaném kódu přímo, obcházení mechanismy zabezpečení CLR. Další informace najdete v tématu [zabezpečení rozhraní .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## <a name="c-interop"></a>interoperabilita C++  
 Interoperabilita C++, také známé jako jeho právě funguje (IJW), můžete použít k zabalení nativních tříd jazyka C++, takže mohou být spotřebovávána kód, který je vytvořené v C# nebo jiném jazyce rozhraní .NET Framework. K tomuto účelu můžete napsat kód C++ zabalit nativní knihovny DLL nebo klasické komponenty COM. Na rozdíl od jiných jazyků rozhraní .NET Framework [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] má interoperabilita podporovat, umožňuje spravovaných a nespravovaných kódu být umístěné ve stejné aplikaci a to i ve stejném souboru. Pak vytvoříte kód C++ pomocí **/CLR** přepínače kompilátoru k vytvoření spravované sestavení. Nakonec můžete přidat odkaz na sestavení v projektu C# a používat zabalené objekty stejně, jako byste použili jiné spravované třídy.  
  
## <a name="exposing-com-components-to-c"></a>Vystavení součástí COM v C#  
 Můžete využívat komponenty modelu COM z projektu C#. Obecné kroky jsou následující:  
  
1.  Vyhledejte komponenty modelu COM pomocí a zaregistrovat ho. Použijte regsvr32.exe k registraci nebo zrušení – registrace knihovny DLL COM.  
  
2.  Přidejte do projektu odkaz na knihovnu COM součásti nebo typu.  
  
     Když přidáte odkaz na [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] používá [Tlbimp.exe (Importér knihovny)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382), což trvá knihovny typů jako vstup do výstupního sestavení vzájemné spolupráce rozhraní .NET Framework. Sestavení, také s názvem obálka volatelná na za běhu (RCW), obsahuje spravované třídy a rozhraní, které balí COM třídy a rozhraní, které jsou v knihovně typu. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]Přidá do projektu odkaz na vygenerované sestavení.  
  
3.  Vytvoření instance třídy, která je definována v RCW. To, se pak vytvoří instanci objektu COM.  
  
4.  Pomocí objektu, stejně jako použít jiné spravované objekty. Pokud je objekt uvolněn systémem uvolňování paměti, instanci objektu COM je také uvolněn z paměti.  
  
 Další informace najdete v tématu [vystavení součástí COM v rozhraní .NET Framework](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730).  
  
## <a name="exposing-c-to-com"></a>Vystavení C# do modelu COM  
 Klienti COM spotřebovat typy C#, které správně zobrazeny. Základní kroky ke zveřejnění typy C# jsou následující:  
  
1.  Přidání atributů spolupráce v projektu jazyka C#.  
  
     Pak lze zobrazit sestavení modelu COM změnou [!INCLUDE[csprcs](~/includes/csprcs-md.md)] vlastnosti projektu. Další informace najdete v tématu [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Generovat knihovny typů COM a zaregistrovat ji COM využití.  
  
     Můžete upravit [!INCLUDE[csprcs](~/includes/csprcs-md.md)] projektu vlastnosti na automatickou registraci sestavení C# pro zprostředkovatel komunikace s objekty COM. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]používá [Regasm.exe (Nástroj registrace sestavení)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)pomocí `/tlb` přepínač příkazového řádku, který přebírá spravované sestavení jako vstup, vytvoření knihovny typů. Popisuje této knihovny typů `public` typy v sestavení a přidá položky registru tak, aby klienti COM můžete vytvořit spravované třídy.  
  
 Další informace najdete v tématu [vystavení komponent architektury .NET Framework do modelu COM](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6) a [Ukázka třídy COM](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Zlepšení výkonu interoperability](http://go.microsoft.com/fwlink/?LinkId=99564)  
 [Představení zprostředkovatele komunikace s objekty COM](http://go.microsoft.com/fwlink/?LinkId=112406)  
 [Zařazování mezi spravovanými a nespravovanými kódu](http://go.microsoft.com/fwlink/?LinkId=112398)  
 [Spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md)  
 [Interoperabilita modelů COM Upřesnit](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
