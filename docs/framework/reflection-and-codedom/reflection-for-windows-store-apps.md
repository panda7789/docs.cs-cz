---
title: Reflexe v rozhraní .NET Framework pro aplikace pro Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9edab859900bf2001956045a5285801bb61d310
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045944"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Reflexe v rozhraní .NET Framework pro aplikace pro Windows Store
Počínaje .NET Framework 4,5 .NET Framework obsahuje sadu typů reflexe a členů pro použití v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacích. Tyto typy a členy jsou k dispozici v plném .NET Framework a také v [rozhraní .NET pro aplikace pro Windows Store](https://go.microsoft.com/fwlink/?LinkID=225700). Tento dokument popisuje hlavní rozdíly mezi těmito položkami a jejich protějšky v rozhraní .NET Framework 4 a dřívějších verzích.  
  
 Pokud vytváříte aplikaci pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], je nutné použít typy a členy reflexe v rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Tyto typy a členy jsou také k dispozici, ačkoli nejsou vyžadovány, pro použití v aplikacích pracovní plochy, takže lze použít stejný kód pro oba typy aplikací.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo a načítání sestavení  
 V rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] třída <xref:System.Reflection.TypeInfo> obsahuje některé funkce třídy <xref:System.Type> rozhraní .NET Framework 4. Objekt <xref:System.Type> představuje odkaz na definici typu, zatímco objekt <xref:System.Reflection.TypeInfo> představuje samotnou definici typu. To umožňuje práci s objekty typu <xref:System.Type> bez toho, aby modul runtime musel načíst sestavení, na které odkazují. Získání přidruženého objektu <xref:System.Reflection.TypeInfo> vynutí načtení sestavení.  
  
 Typ <xref:System.Reflection.TypeInfo> obsahuje mnoho členů, jež jsou k dispozici v typu <xref:System.Type>, a mnoho vlastností reflexe rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] vrací kolekce objektů <xref:System.Reflection.TypeInfo>. Chcete-li získat objekt <xref:System.Reflection.TypeInfo> z objektu <xref:System.Type>, použijte metodu <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Metody dotazů  
 V rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] použijte vlastnosti reflexe, které vrací kolekce typu <xref:System.Collections.Generic.IEnumerable%601>, namísto metod, které vrací pole. Kontexty reflexe mohou pro velká sestavení nebo typy implementovat opožděné procházení těchto kolekcí.  
  
 Vlastnosti reflexe vrací pouze metody deklarované pro daný objekt namísto procházení stromu dědičnosti. Kromě toho nelze pro filtrování použít parametry <xref:System.Reflection.BindingFlags>. Namísto toho filtrování probíhá na vrácené kolekci v uživatelském kódu pomocí dotazů LINQ. Pro objekty reflexe modulu runtime (například výsledek výrazu `typeof(Object)`) je procházení stromu dědičnosti provedeno nejlépe prostřednictvím pomocných metod třídy <xref:System.Reflection.RuntimeReflectionExtensions>. Spotřebitelé objektů z vlastních kontextů reflexe nemohou tyto metody použít a musí strom dědičnosti procházet sami.  
  
## <a name="restrictions"></a>Omezení  
 V aplikaci pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] je přístup k některým typům a členům rozhraní .NET Framework omezen. Například pomocí objektu [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] nelze volat metody rozhraní .NET Framework, které nejsou zahrnuty v rozhraní <xref:System.Reflection.MethodInfo>. Také některé typy a členy, které nejsou v rámci aplikace pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] považovány za bezpečné, jsou blokovány, jako například typy <xref:System.Runtime.InteropServices.Marshal> a <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal>. Toto omezení se týká pouze typů a členů rozhraní .NET Framework. Váš kód nebo kód třetích stran lze volat jako obvykle.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá typy a členy reflexe rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] k načtení metod a vlastností typu <xref:System.Globalization.Calendar>, včetně odvozených metod a vlastností. Chcete-li spustit tento kód, vložte jej do souboru kódu pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] stránku, která <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> obsahuje ovládací prvek `textblock1` pojmenovaný v projektu s názvem reflexe. Pokud vložíte tento kód do projektu s jiným názvem, je třeba změnit název oboru názvů tak, aby odpovídal vašemu projektu.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Reflexe](reflection.md)
- [.NET pro aplikace pro Windows Store – podporovaná rozhraní API](https://go.microsoft.com/fwlink/?LinkID=225700)
