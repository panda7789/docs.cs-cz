---
title: BindingSource – přehled komponenty
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
ms.openlocfilehash: bd1b38b434f9932a575745d7a1761ff18b009115
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917815"
---
# <a name="bindingsource-component-overview"></a>BindingSource – přehled komponenty
<xref:System.Windows.Forms.BindingSource> Komponenta je navržena tak, aby zjednodušila proces vazby ovládacích prvků k základnímu zdroji dat. <xref:System.Windows.Forms.BindingSource> Komponenta funguje jako přenosový i zdroj dat pro jiné ovládací prvky, na které lze vytvořit vazby. Poskytuje abstrakci datového připojení formuláře při předávání příkazů do základního seznamu dat. Kromě toho můžete přímo do něj přidat data, aby součást sama fungovala jako zdroj dat.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>Komponenta BindingSource jako prostředník  
 <xref:System.Windows.Forms.BindingSource> Komponenta slouží jako zdroj dat pro některé nebo všechny ovládací prvky ve formuláři. V aplikaci Visual Studio <xref:System.Windows.Forms.BindingSource> může být svázán s ovládacím prvkem prostřednictvím `DataBindings` vlastnosti, která je přístupná z okna **vlastnosti** . Podívejte [se také na postupy: Pomocí návrháře](bind-wf-controls-with-the-bindingsource.md)navažte ovládací prvky model Windows Forms s komponentou BindingSource.  
  
 <xref:System.Windows.Forms.BindingSource> Komponentu můžete navazovat na jednoduché zdroje dat, jako je jediná vlastnost objektu nebo základní kolekce, jako <xref:System.Collections.ArrayList>je například databázová tabulka. <xref:System.Windows.Forms.BindingSource> Komponenta funguje jako prostředník, který poskytuje služby pro vázání a správu měn. V době návrhu nebo v době spuštění můžete vytvořit vazby <xref:System.Windows.Forms.BindingSource> komponenty ke složitému zdroji dat <xref:System.Windows.Forms.BindingSource.DataSource%2A> nastavením vlastností a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastností na databázi a tabulku v uvedeném pořadí. Následující obrázek ukazuje, kde se <xref:System.Windows.Forms.BindingSource> komponenta zahodí do existující architektury datové vazby.  
  
 ![Vazba struktury zdroje a vazby dat](./media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
> V době návrhu některé akce, jako je například přetažení databázové tabulky z okna dat do prázdného formuláře, vytvoří <xref:System.Windows.Forms.BindingSource> komponentu, sváže ji s podkladovým zdrojem dat a přidávají ovládací prvky pro práci s daty vše v jedné operaci. Viz také [ovládací prvky Bind model Windows Forms pro data v aplikaci Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>Komponenta BindingSource jako zdroj dat  
 Pokud začnete přidávat položky do <xref:System.Windows.Forms.BindingSource> komponenty bez prvotního určení seznamu, ke kterému má být vázáno, bude tato součást fungovat jako zdroj dat ve stylu seznamu a přijímá tyto přidané položky.  
  
 Kromě toho můžete napsat kód pro poskytnutí vlastní funkce "AddNew" prostřednictvím <xref:System.Windows.Forms.BindingSource.AddingNew> události, která je vyvolána, <xref:System.Windows.Forms.BindingSource.AddNew%2A> když je metoda volána před přidáním položky do seznamu. Další informace najdete v tématu [architektura komponenty BindingSource](bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Navigace  
 Pro uživatele, kteří potřebují navigovat data ve formuláři, <xref:System.Windows.Forms.BindingNavigator> vám komponenta umožňuje procházet a manipulovat <xref:System.Windows.Forms.BindingSource> s daty v koordinaci s komponentou. Další informace najdete v tématu [BindingNavigator – ovládací prvek](bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Manipulace s daty  
 : <xref:System.Windows.Forms.BindingSource> Funguje<xref:System.Windows.Forms.CurrencyManager> jako pro všechny své vazby a může proto poskytnout přístup k informacím o měně a pozici v souvislosti se zdrojem dat. Následující tabulka uvádí členy, které <xref:System.Windows.Forms.BindingSource> komponenta poskytuje pro přístup k podkladovým datům a manipulaci s nimi.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Current%2A>majetek|Načte aktuální položku zdroje dat.|  
|<xref:System.Windows.Forms.BindingSource.Position%2A>majetek|Získá nebo nastaví aktuální pozici v podkladovém seznamu.|  
|<xref:System.Windows.Forms.BindingSource.List%2A>majetek|Získá seznam, který je vyhodnocování <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vyhodnocení. Pokud <xref:System.Windows.Forms.BindingSource.DataMember%2A> parametr není nastaven, vrátí seznam určený parametrem <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|<xref:System.Windows.Forms.BindingSource.Insert%2A>Metoda|Vloží položku ze seznamu na zadaný index.|  
|<xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>Metoda|Odebere aktuální položku ze seznamu.|  
|<xref:System.Windows.Forms.BindingSource.EndEdit%2A>Metoda|Použije nedokončené změny v podkladovém zdroji dat.|  
|<xref:System.Windows.Forms.BindingSource.CancelEdit%2A>Metoda|Zruší aktuální operaci úprav.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A>Metoda|Přidá novou položku do základního seznamu. Pokud zdroj dat implementuje <xref:System.ComponentModel.IBindingList> a vrátí položku <xref:System.Windows.Forms.BindingSource.AddingNew> z události, přidá tuto položku. V opačném případě je požadavek předán <xref:System.ComponentModel.IBindingList.AddNew%2A> metodě seznamu. Pokud základní seznam <xref:System.ComponentModel.IBindingList>není, položka se automaticky vytvoří prostřednictvím veřejného konstruktoru bez parametrů.|  
  
## <a name="sorting-and-filtering"></a>Řazení a filtrování  
 Obvykle byste měli pracovat s uspořádaným nebo filtrovaným zobrazením zdroje dat. Následující tabulka uvádí členy, které <xref:System.Windows.Forms.BindingSource> poskytuje zdroj dat součásti.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A>majetek|Pokud je zdrojem dat objekt <xref:System.ComponentModel.IBindingList>, získá nebo nastaví název sloupce, který se používá k řazení a řazení informací o objednávkách. Pokud je <xref:System.ComponentModel.IBindingListView> zdrojem dat a podporuje pokročilé řazení, získá více názvů sloupců používaných k řazení a seřazení informací o objednávkách.|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A>majetek|Pokud je zdrojem dat objekt <xref:System.ComponentModel.IBindingListView>, získá nebo nastaví výraz použitý k filtrování zobrazených řádků.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Architektura komponenty BindingSource](bindingsource-component-architecture.md)
- [Komponenta BindingSource](bindingsource-component.md)
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
