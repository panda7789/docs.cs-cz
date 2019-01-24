---
title: Kolekce schémat OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f753f35aab0a0200da5de463a73abb9813253d11
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658452"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="4d3ad-102">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="4d3ad-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="4d3ad-103">Tato část popisuje kolekci podpora schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="4d3ad-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="4d3ad-104">Zprostředkovatel Microsoft SQL serveru OLE DB</span><span class="sxs-lookup"><span data-stu-id="4d3ad-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="4d3ad-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="4d3ad-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="4d3ad-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4d3ad-106">Tables</span></span>  
  
-   <span data-ttu-id="4d3ad-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-107">Columns</span></span>  
  
-   <span data-ttu-id="4d3ad-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="4d3ad-108">Procedures</span></span>  
  
-   <span data-ttu-id="4d3ad-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4d3ad-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="4d3ad-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="4d3ad-110">Catalog</span></span>  
  
-   <span data-ttu-id="4d3ad-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="4d3ad-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="4d3ad-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4d3ad-112">Tables</span></span>  
  
|<span data-ttu-id="4d3ad-113">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-113">ColumnName</span></span>|<span data-ttu-id="4d3ad-114">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-115">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-116">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-116">String</span></span>|  
|<span data-ttu-id="4d3ad-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-118">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-118">String</span></span>|  
|<span data-ttu-id="4d3ad-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-119">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-120">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-120">String</span></span>|  
|<span data-ttu-id="4d3ad-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-121">TABLE_TYPE</span></span>|<span data-ttu-id="4d3ad-122">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-122">String</span></span>|  
|<span data-ttu-id="4d3ad-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-123">TABLE_GUID</span></span>|<span data-ttu-id="4d3ad-124">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-124">Guid</span></span>|  
|<span data-ttu-id="4d3ad-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-125">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-126">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-126">String</span></span>|  
|<span data-ttu-id="4d3ad-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-127">TABLE_PROPID</span></span>|<span data-ttu-id="4d3ad-128">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-128">Int64</span></span>|  
|<span data-ttu-id="4d3ad-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-129">DATE_CREATED</span></span>|<span data-ttu-id="4d3ad-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-130">DateTime</span></span>|  
|<span data-ttu-id="4d3ad-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-131">DATE_MODIFIED</span></span>|<span data-ttu-id="4d3ad-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="4d3ad-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-133">Columns</span></span>  
  
|<span data-ttu-id="4d3ad-134">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-134">ColumnName</span></span>|<span data-ttu-id="4d3ad-135">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-136">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-137">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-137">String</span></span>|  
|<span data-ttu-id="4d3ad-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-139">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-139">String</span></span>|  
|<span data-ttu-id="4d3ad-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-140">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-141">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-141">String</span></span>|  
|<span data-ttu-id="4d3ad-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-142">COLUMN_NAME</span></span>|<span data-ttu-id="4d3ad-143">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-143">String</span></span>|  
|<span data-ttu-id="4d3ad-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-144">COLUMN_GUID</span></span>|<span data-ttu-id="4d3ad-145">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-145">Guid</span></span>|  
|<span data-ttu-id="4d3ad-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-146">COLUMN_PROPID</span></span>|<span data-ttu-id="4d3ad-147">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-147">Int64</span></span>|  
|<span data-ttu-id="4d3ad-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="4d3ad-149">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-149">Int64</span></span>|  
|<span data-ttu-id="4d3ad-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="4d3ad-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="4d3ad-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-151">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="4d3ad-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="4d3ad-153">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-153">String</span></span>|  
|<span data-ttu-id="4d3ad-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="4d3ad-155">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-155">Int64</span></span>|  
|<span data-ttu-id="4d3ad-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-156">IS_NULLABLE</span></span>|<span data-ttu-id="4d3ad-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-157">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-158">DATA_TYPE</span></span>|<span data-ttu-id="4d3ad-159">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-159">Int32</span></span>|  
|<span data-ttu-id="4d3ad-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-160">TYPE_GUID</span></span>|<span data-ttu-id="4d3ad-161">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-161">Guid</span></span>|  
|<span data-ttu-id="4d3ad-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="4d3ad-163">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-163">Int64</span></span>|  
|<span data-ttu-id="4d3ad-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="4d3ad-165">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-165">Int64</span></span>|  
|<span data-ttu-id="4d3ad-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="4d3ad-167">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-167">Int32</span></span>|  
|<span data-ttu-id="4d3ad-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="4d3ad-169">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-169">Int16</span></span>|  
|<span data-ttu-id="4d3ad-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="4d3ad-171">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-171">Int64</span></span>|  
|<span data-ttu-id="4d3ad-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="4d3ad-173">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-173">String</span></span>|  
|<span data-ttu-id="4d3ad-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="4d3ad-175">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-175">String</span></span>|  
|<span data-ttu-id="4d3ad-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="4d3ad-177">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-177">String</span></span>|  
|<span data-ttu-id="4d3ad-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="4d3ad-179">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-179">String</span></span>|  
|<span data-ttu-id="4d3ad-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="4d3ad-181">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-181">String</span></span>|  
|<span data-ttu-id="4d3ad-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-182">COLLATION_NAME</span></span>|<span data-ttu-id="4d3ad-183">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-183">String</span></span>|  
|<span data-ttu-id="4d3ad-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="4d3ad-185">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-185">String</span></span>|  
|<span data-ttu-id="4d3ad-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="4d3ad-187">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-187">String</span></span>|  
|<span data-ttu-id="4d3ad-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-188">DOMAIN_NAME</span></span>|<span data-ttu-id="4d3ad-189">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-189">String</span></span>|  
|<span data-ttu-id="4d3ad-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-190">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-191">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-191">String</span></span>|  
|<span data-ttu-id="4d3ad-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-192">COLUMN_LCID</span></span>|<span data-ttu-id="4d3ad-193">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-193">Int32</span></span>|  
|<span data-ttu-id="4d3ad-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="4d3ad-195">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-195">Int32</span></span>|  
|<span data-ttu-id="4d3ad-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-196">COLUMN_SORTID</span></span>|<span data-ttu-id="4d3ad-197">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-197">Int32</span></span>|  
|<span data-ttu-id="4d3ad-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="4d3ad-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="4d3ad-199">Byte[]</span></span>|  
|<span data-ttu-id="4d3ad-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-200">IS_COMPUTED</span></span>|<span data-ttu-id="4d3ad-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="4d3ad-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="4d3ad-202">Procedures</span></span>  
  
|<span data-ttu-id="4d3ad-203">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-203">ColumnName</span></span>|<span data-ttu-id="4d3ad-204">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="4d3ad-206">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-206">String</span></span>|  
|<span data-ttu-id="4d3ad-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-208">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-208">String</span></span>|  
|<span data-ttu-id="4d3ad-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="4d3ad-210">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-210">String</span></span>|  
|<span data-ttu-id="4d3ad-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4d3ad-212">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-212">Int16</span></span>|  
|<span data-ttu-id="4d3ad-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="4d3ad-214">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-214">String</span></span>|  
|<span data-ttu-id="4d3ad-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-215">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-216">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-216">String</span></span>|  
|<span data-ttu-id="4d3ad-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-217">DATE_CREATED</span></span>|<span data-ttu-id="4d3ad-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-218">DateTime</span></span>|  
|<span data-ttu-id="4d3ad-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-219">DATE_MODIFIED</span></span>|<span data-ttu-id="4d3ad-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="4d3ad-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4d3ad-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="4d3ad-222">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-222">ColumnName</span></span>|<span data-ttu-id="4d3ad-223">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="4d3ad-225">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-225">String</span></span>|  
|<span data-ttu-id="4d3ad-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-227">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-227">String</span></span>|  
|<span data-ttu-id="4d3ad-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="4d3ad-229">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-229">String</span></span>|  
|<span data-ttu-id="4d3ad-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-230">PARAMETER_NAME</span></span>|<span data-ttu-id="4d3ad-231">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-231">String</span></span>|  
|<span data-ttu-id="4d3ad-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="4d3ad-233">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-233">Int32</span></span>|  
|<span data-ttu-id="4d3ad-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="4d3ad-235">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-235">Int32</span></span>|  
|<span data-ttu-id="4d3ad-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="4d3ad-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="4d3ad-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-237">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="4d3ad-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="4d3ad-239">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-239">String</span></span>|  
|<span data-ttu-id="4d3ad-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-240">IS_NULLABLE</span></span>|<span data-ttu-id="4d3ad-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-241">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-242">DATA_TYPE</span></span>|<span data-ttu-id="4d3ad-243">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-243">Int32</span></span>|  
|<span data-ttu-id="4d3ad-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="4d3ad-245">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-245">Int64</span></span>|  
|<span data-ttu-id="4d3ad-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="4d3ad-247">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-247">Int64</span></span>|  
|<span data-ttu-id="4d3ad-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="4d3ad-249">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-249">Int32</span></span>|  
|<span data-ttu-id="4d3ad-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="4d3ad-251">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-251">Int16</span></span>|  
|<span data-ttu-id="4d3ad-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-252">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-253">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-253">String</span></span>|  
|<span data-ttu-id="4d3ad-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-254">TYPE_NAME</span></span>|<span data-ttu-id="4d3ad-255">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-255">String</span></span>|  
|<span data-ttu-id="4d3ad-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="4d3ad-257">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="4d3ad-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="4d3ad-258">Catalog</span></span>  
  
|<span data-ttu-id="4d3ad-259">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-259">ColumnName</span></span>|<span data-ttu-id="4d3ad-260">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-261">CATALOG_NAME</span></span>|<span data-ttu-id="4d3ad-262">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-262">String</span></span>|  
|<span data-ttu-id="4d3ad-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-263">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-264">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="4d3ad-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="4d3ad-265">Indexes</span></span>  
  
|<span data-ttu-id="4d3ad-266">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-266">ColumnName</span></span>|<span data-ttu-id="4d3ad-267">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-268">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-269">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-269">String</span></span>|  
|<span data-ttu-id="4d3ad-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-271">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-271">String</span></span>|  
|<span data-ttu-id="4d3ad-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-272">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-273">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-273">String</span></span>|  
|<span data-ttu-id="4d3ad-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-274">INDEX_CATALOG</span></span>|<span data-ttu-id="4d3ad-275">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-275">String</span></span>|  
|<span data-ttu-id="4d3ad-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="4d3ad-277">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-277">String</span></span>|  
|<span data-ttu-id="4d3ad-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-278">INDEX_NAME</span></span>|<span data-ttu-id="4d3ad-279">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-279">String</span></span>|  
|<span data-ttu-id="4d3ad-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="4d3ad-280">PRIMARY_KEY</span></span>|<span data-ttu-id="4d3ad-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-281">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-282">UNIQUE</span></span>|<span data-ttu-id="4d3ad-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-283">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-284">CLUSTERED</span></span>|<span data-ttu-id="4d3ad-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-285">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-286">TYP</span><span class="sxs-lookup"><span data-stu-id="4d3ad-286">TYPE</span></span>|<span data-ttu-id="4d3ad-287">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-287">Int32</span></span>|  
|<span data-ttu-id="4d3ad-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="4d3ad-288">FILL_FACTOR</span></span>|<span data-ttu-id="4d3ad-289">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-289">Int32</span></span>|  
|<span data-ttu-id="4d3ad-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-290">INITIAL_SIZE</span></span>|<span data-ttu-id="4d3ad-291">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-291">Int32</span></span>|  
|<span data-ttu-id="4d3ad-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-292">NULLS</span></span>|<span data-ttu-id="4d3ad-293">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-293">Int32</span></span>|  
|<span data-ttu-id="4d3ad-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="4d3ad-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-295">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-296">AUTO_UPDATE</span></span>|<span data-ttu-id="4d3ad-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-297">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-298">NULL_COLLATION</span></span>|<span data-ttu-id="4d3ad-299">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-299">Int32</span></span>|  
|<span data-ttu-id="4d3ad-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="4d3ad-301">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-301">Int64</span></span>|  
|<span data-ttu-id="4d3ad-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-302">COLUMN_NAME</span></span>|<span data-ttu-id="4d3ad-303">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-303">String</span></span>|  
|<span data-ttu-id="4d3ad-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-304">COLUMN_GUID</span></span>|<span data-ttu-id="4d3ad-305">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-305">Guid</span></span>|  
|<span data-ttu-id="4d3ad-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-306">COLUMN_PROPID</span></span>|<span data-ttu-id="4d3ad-307">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-307">Int64</span></span>|  
|<span data-ttu-id="4d3ad-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-308">COLLATION</span></span>|<span data-ttu-id="4d3ad-309">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-309">Int16</span></span>|  
|<span data-ttu-id="4d3ad-310">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-310">CARDINALITY</span></span>|<span data-ttu-id="4d3ad-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="4d3ad-311">Decimal</span></span>|  
|<span data-ttu-id="4d3ad-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="4d3ad-312">PAGES</span></span>|<span data-ttu-id="4d3ad-313">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-313">Int32</span></span>|  
|<span data-ttu-id="4d3ad-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-314">FILTER_CONDITION</span></span>|<span data-ttu-id="4d3ad-315">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-315">String</span></span>|  
|<span data-ttu-id="4d3ad-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="4d3ad-316">INTEGRATED</span></span>|<span data-ttu-id="4d3ad-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="4d3ad-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="4d3ad-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="4d3ad-319">Oracle OLE DB ovladač Microsoft podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="4d3ad-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="4d3ad-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4d3ad-320">Tables</span></span>  
  
-   <span data-ttu-id="4d3ad-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-321">Columns</span></span>  
  
-   <span data-ttu-id="4d3ad-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="4d3ad-322">Procedures</span></span>  
  
-   <span data-ttu-id="4d3ad-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4d3ad-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="4d3ad-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4d3ad-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="4d3ad-325">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="4d3ad-325">Views</span></span>  
  
-   <span data-ttu-id="4d3ad-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="4d3ad-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="4d3ad-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4d3ad-327">Tables</span></span>  
  
|<span data-ttu-id="4d3ad-328">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-328">ColumnName</span></span>|<span data-ttu-id="4d3ad-329">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-330">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-331">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-331">String</span></span>|  
|<span data-ttu-id="4d3ad-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-333">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-333">String</span></span>|  
|<span data-ttu-id="4d3ad-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-334">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-335">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-335">String</span></span>|  
|<span data-ttu-id="4d3ad-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-336">TABLE_TYPE</span></span>|<span data-ttu-id="4d3ad-337">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-337">String</span></span>|  
|<span data-ttu-id="4d3ad-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-338">TABLE_GUID</span></span>|<span data-ttu-id="4d3ad-339">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-339">Guid</span></span>|  
|<span data-ttu-id="4d3ad-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-340">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-341">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-341">String</span></span>|  
|<span data-ttu-id="4d3ad-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-342">TABLE_PROPID</span></span>|<span data-ttu-id="4d3ad-343">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-343">Int64</span></span>|  
|<span data-ttu-id="4d3ad-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-344">DATE_CREATED</span></span>|<span data-ttu-id="4d3ad-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-345">DateTime</span></span>|  
|<span data-ttu-id="4d3ad-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-346">DATE_MODIFIED</span></span>|<span data-ttu-id="4d3ad-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="4d3ad-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-348">Columns</span></span>  
  
|<span data-ttu-id="4d3ad-349">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-349">ColumnName</span></span>|<span data-ttu-id="4d3ad-350">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-351">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-352">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-352">String</span></span>|  
|<span data-ttu-id="4d3ad-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-354">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-354">String</span></span>|  
|<span data-ttu-id="4d3ad-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-355">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-356">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-356">String</span></span>|  
|<span data-ttu-id="4d3ad-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-357">COLUMN_NAME</span></span>|<span data-ttu-id="4d3ad-358">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-358">String</span></span>|  
|<span data-ttu-id="4d3ad-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-359">COLUMN_GUID</span></span>|<span data-ttu-id="4d3ad-360">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-360">Guid</span></span>|  
|<span data-ttu-id="4d3ad-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-361">COLUMN_PROPID</span></span>|<span data-ttu-id="4d3ad-362">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-362">Int64</span></span>|  
|<span data-ttu-id="4d3ad-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="4d3ad-364">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-364">Int64</span></span>|  
|<span data-ttu-id="4d3ad-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="4d3ad-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="4d3ad-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-366">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="4d3ad-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="4d3ad-368">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-368">String</span></span>|  
|<span data-ttu-id="4d3ad-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="4d3ad-370">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-370">Int64</span></span>|  
|<span data-ttu-id="4d3ad-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-371">IS_NULLABLE</span></span>|<span data-ttu-id="4d3ad-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-372">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-373">DATA_TYPE</span></span>|<span data-ttu-id="4d3ad-374">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-374">Int32</span></span>|  
|<span data-ttu-id="4d3ad-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-375">TYPE_GUID</span></span>|<span data-ttu-id="4d3ad-376">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-376">Guid</span></span>|  
|<span data-ttu-id="4d3ad-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="4d3ad-378">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-378">Int64</span></span>|  
|<span data-ttu-id="4d3ad-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="4d3ad-380">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-380">Int64</span></span>|  
|<span data-ttu-id="4d3ad-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="4d3ad-382">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-382">Int32</span></span>|  
|<span data-ttu-id="4d3ad-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="4d3ad-384">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-384">Int16</span></span>|  
|<span data-ttu-id="4d3ad-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="4d3ad-386">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-386">Int64</span></span>|  
|<span data-ttu-id="4d3ad-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="4d3ad-388">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-388">String</span></span>|  
|<span data-ttu-id="4d3ad-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="4d3ad-390">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-390">String</span></span>|  
|<span data-ttu-id="4d3ad-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="4d3ad-392">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-392">String</span></span>|  
|<span data-ttu-id="4d3ad-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="4d3ad-394">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-394">String</span></span>|  
|<span data-ttu-id="4d3ad-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="4d3ad-396">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-396">String</span></span>|  
|<span data-ttu-id="4d3ad-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-397">COLLATION_NAME</span></span>|<span data-ttu-id="4d3ad-398">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-398">String</span></span>|  
|<span data-ttu-id="4d3ad-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="4d3ad-400">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-400">String</span></span>|  
|<span data-ttu-id="4d3ad-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="4d3ad-402">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-402">String</span></span>|  
|<span data-ttu-id="4d3ad-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-403">DOMAIN_NAME</span></span>|<span data-ttu-id="4d3ad-404">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-404">String</span></span>|  
|<span data-ttu-id="4d3ad-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-405">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-406">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="4d3ad-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="4d3ad-407">Procedures</span></span>  
  
|<span data-ttu-id="4d3ad-408">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-408">ColumnName</span></span>|<span data-ttu-id="4d3ad-409">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="4d3ad-411">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-411">String</span></span>|  
|<span data-ttu-id="4d3ad-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-413">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-413">String</span></span>|  
|<span data-ttu-id="4d3ad-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="4d3ad-415">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-415">String</span></span>|  
|<span data-ttu-id="4d3ad-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4d3ad-417">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-417">Int16</span></span>|  
|<span data-ttu-id="4d3ad-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="4d3ad-419">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-419">String</span></span>|  
|<span data-ttu-id="4d3ad-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-420">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-421">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-421">String</span></span>|  
|<span data-ttu-id="4d3ad-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-422">DATE_CREATED</span></span>|<span data-ttu-id="4d3ad-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-423">DateTime</span></span>|  
|<span data-ttu-id="4d3ad-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-424">DATE_MODIFIED</span></span>|<span data-ttu-id="4d3ad-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="4d3ad-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4d3ad-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="4d3ad-427">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-427">ColumnName</span></span>|<span data-ttu-id="4d3ad-428">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="4d3ad-430">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-430">String</span></span>|  
|<span data-ttu-id="4d3ad-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-432">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-432">String</span></span>|  
|<span data-ttu-id="4d3ad-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="4d3ad-434">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-434">String</span></span>|  
|<span data-ttu-id="4d3ad-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-435">COLUMN_NAME</span></span>|<span data-ttu-id="4d3ad-436">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-436">String</span></span>|  
|<span data-ttu-id="4d3ad-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-437">COLUMN_GUID</span></span>|<span data-ttu-id="4d3ad-438">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-438">Guid</span></span>|  
|<span data-ttu-id="4d3ad-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-439">COLUMN_PROPID</span></span>|<span data-ttu-id="4d3ad-440">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-440">Int64</span></span>|  
|<span data-ttu-id="4d3ad-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="4d3ad-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="4d3ad-442">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-442">Int64</span></span>|  
|<span data-ttu-id="4d3ad-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="4d3ad-444">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-444">Int64</span></span>|  
|<span data-ttu-id="4d3ad-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-445">IS_NULLABLE</span></span>|<span data-ttu-id="4d3ad-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-446">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-447">DATA_TYPE</span></span>|<span data-ttu-id="4d3ad-448">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-448">Int32</span></span>|  
|<span data-ttu-id="4d3ad-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-449">TYPE_GUID</span></span>|<span data-ttu-id="4d3ad-450">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-450">Guid</span></span>|  
|<span data-ttu-id="4d3ad-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="4d3ad-452">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-452">Int64</span></span>|  
|<span data-ttu-id="4d3ad-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="4d3ad-454">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-454">Int64</span></span>|  
|<span data-ttu-id="4d3ad-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="4d3ad-456">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-456">Int32</span></span>|  
|<span data-ttu-id="4d3ad-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="4d3ad-458">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-458">Int16</span></span>|  
|<span data-ttu-id="4d3ad-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-459">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-460">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-460">String</span></span>|  
|<span data-ttu-id="4d3ad-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="4d3ad-461">OVERLOAD</span></span>|<span data-ttu-id="4d3ad-462">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="4d3ad-463">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="4d3ad-463">Views</span></span>  
  
|<span data-ttu-id="4d3ad-464">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-464">ColumnName</span></span>|<span data-ttu-id="4d3ad-465">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-466">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-467">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-467">String</span></span>|  
|<span data-ttu-id="4d3ad-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-469">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-469">String</span></span>|  
|<span data-ttu-id="4d3ad-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-470">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-471">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-471">String</span></span>|  
|<span data-ttu-id="4d3ad-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="4d3ad-473">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-473">String</span></span>|  
|<span data-ttu-id="4d3ad-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-474">CHECK_OPTION</span></span>|<span data-ttu-id="4d3ad-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-475">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-476">IS_UPDATABLE</span></span>|<span data-ttu-id="4d3ad-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-477">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-478">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-479">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-479">String</span></span>|  
|<span data-ttu-id="4d3ad-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-480">DATE_CREATED</span></span>|<span data-ttu-id="4d3ad-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-481">DateTime</span></span>|  
|<span data-ttu-id="4d3ad-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-482">DATE_MODIFIED</span></span>|<span data-ttu-id="4d3ad-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="4d3ad-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="4d3ad-484">Indexes</span></span>  
  
|<span data-ttu-id="4d3ad-485">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-485">ColumnName</span></span>|<span data-ttu-id="4d3ad-486">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-487">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-488">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-488">String</span></span>|  
|<span data-ttu-id="4d3ad-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-490">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-490">String</span></span>|  
|<span data-ttu-id="4d3ad-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-491">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-492">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-492">String</span></span>|  
|<span data-ttu-id="4d3ad-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-493">INDEX_CATALOG</span></span>|<span data-ttu-id="4d3ad-494">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-494">String</span></span>|  
|<span data-ttu-id="4d3ad-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="4d3ad-496">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-496">String</span></span>|  
|<span data-ttu-id="4d3ad-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-497">INDEX_NAME</span></span>|<span data-ttu-id="4d3ad-498">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-498">String</span></span>|  
|<span data-ttu-id="4d3ad-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="4d3ad-499">PRIMARY_KEY</span></span>|<span data-ttu-id="4d3ad-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-500">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-501">UNIQUE</span></span>|<span data-ttu-id="4d3ad-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-502">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-503">CLUSTERED</span></span>|<span data-ttu-id="4d3ad-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-504">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-505">TYP</span><span class="sxs-lookup"><span data-stu-id="4d3ad-505">TYPE</span></span>|<span data-ttu-id="4d3ad-506">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-506">Int32</span></span>|  
|<span data-ttu-id="4d3ad-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="4d3ad-507">FILL_FACTOR</span></span>|<span data-ttu-id="4d3ad-508">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-508">Int32</span></span>|  
|<span data-ttu-id="4d3ad-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-509">INITIAL_SIZE</span></span>|<span data-ttu-id="4d3ad-510">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-510">Int32</span></span>|  
|<span data-ttu-id="4d3ad-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-511">NULLS</span></span>|<span data-ttu-id="4d3ad-512">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-512">Int32</span></span>|  
|<span data-ttu-id="4d3ad-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="4d3ad-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-514">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-515">AUTO_UPDATE</span></span>|<span data-ttu-id="4d3ad-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-516">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-517">NULL_COLLATION</span></span>|<span data-ttu-id="4d3ad-518">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-518">Int32</span></span>|  
|<span data-ttu-id="4d3ad-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="4d3ad-520">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-520">Int64</span></span>|  
|<span data-ttu-id="4d3ad-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-521">COLUMN_NAME</span></span>|<span data-ttu-id="4d3ad-522">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-522">String</span></span>|  
|<span data-ttu-id="4d3ad-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-523">COLUMN_GUID</span></span>|<span data-ttu-id="4d3ad-524">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-524">Guid</span></span>|  
|<span data-ttu-id="4d3ad-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-525">COLUMN_PROPID</span></span>|<span data-ttu-id="4d3ad-526">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-526">Int64</span></span>|  
|<span data-ttu-id="4d3ad-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-527">COLLATION</span></span>|<span data-ttu-id="4d3ad-528">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-528">Int16</span></span>|  
|<span data-ttu-id="4d3ad-529">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-529">CARDINALITY</span></span>|<span data-ttu-id="4d3ad-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="4d3ad-530">Decimal</span></span>|  
|<span data-ttu-id="4d3ad-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="4d3ad-531">PAGES</span></span>|<span data-ttu-id="4d3ad-532">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-532">Int32</span></span>|  
|<span data-ttu-id="4d3ad-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-533">FILTER_CONDITION</span></span>|<span data-ttu-id="4d3ad-534">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-534">String</span></span>|  
|<span data-ttu-id="4d3ad-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="4d3ad-535">INTEGRATED</span></span>|<span data-ttu-id="4d3ad-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="4d3ad-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="4d3ad-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="4d3ad-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="4d3ad-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="4d3ad-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4d3ad-539">Tables</span></span>  
  
-   <span data-ttu-id="4d3ad-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-540">Columns</span></span>  
  
-   <span data-ttu-id="4d3ad-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="4d3ad-541">Procedures</span></span>  
  
-   <span data-ttu-id="4d3ad-542">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="4d3ad-542">Views</span></span>  
  
-   <span data-ttu-id="4d3ad-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="4d3ad-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="4d3ad-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4d3ad-544">Tables</span></span>  
  
|<span data-ttu-id="4d3ad-545">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-545">ColumnName</span></span>|<span data-ttu-id="4d3ad-546">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-547">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-548">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-548">String</span></span>|  
|<span data-ttu-id="4d3ad-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-550">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-550">String</span></span>|  
|<span data-ttu-id="4d3ad-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-551">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-552">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-552">String</span></span>|  
|<span data-ttu-id="4d3ad-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-553">TABLE_TYPE</span></span>|<span data-ttu-id="4d3ad-554">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-554">String</span></span>|  
|<span data-ttu-id="4d3ad-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-555">TABLE_GUID</span></span>|<span data-ttu-id="4d3ad-556">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-556">Guid</span></span>|  
|<span data-ttu-id="4d3ad-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-557">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-558">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-558">String</span></span>|  
|<span data-ttu-id="4d3ad-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-559">TABLE_PROPID</span></span>|<span data-ttu-id="4d3ad-560">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-560">Int64</span></span>|  
|<span data-ttu-id="4d3ad-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-561">DATE_CREATED</span></span>|<span data-ttu-id="4d3ad-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-562">DateTime</span></span>|  
|<span data-ttu-id="4d3ad-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-563">DATE_MODIFIED</span></span>|<span data-ttu-id="4d3ad-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="4d3ad-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-565">Columns</span></span>  
  
|<span data-ttu-id="4d3ad-566">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-566">ColumnName</span></span>|<span data-ttu-id="4d3ad-567">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-568">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-569">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-569">String</span></span>|  
|<span data-ttu-id="4d3ad-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-571">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-571">String</span></span>|  
|<span data-ttu-id="4d3ad-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-572">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-573">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-573">String</span></span>|  
|<span data-ttu-id="4d3ad-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-574">COLUMN_NAME</span></span>|<span data-ttu-id="4d3ad-575">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-575">String</span></span>|  
|<span data-ttu-id="4d3ad-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-576">COLUMN_GUID</span></span>|<span data-ttu-id="4d3ad-577">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-577">Guid</span></span>|  
|<span data-ttu-id="4d3ad-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-578">COLUMN_PROPID</span></span>|<span data-ttu-id="4d3ad-579">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-579">Int64</span></span>|  
|<span data-ttu-id="4d3ad-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="4d3ad-581">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-581">Int64</span></span>|  
|<span data-ttu-id="4d3ad-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="4d3ad-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="4d3ad-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-583">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="4d3ad-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="4d3ad-585">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-585">String</span></span>|  
|<span data-ttu-id="4d3ad-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="4d3ad-587">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-587">Int64</span></span>|  
|<span data-ttu-id="4d3ad-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-588">IS_NULLABLE</span></span>|<span data-ttu-id="4d3ad-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-589">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-590">DATA_TYPE</span></span>|<span data-ttu-id="4d3ad-591">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-591">Int32</span></span>|  
|<span data-ttu-id="4d3ad-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-592">TYPE_GUID</span></span>|<span data-ttu-id="4d3ad-593">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-593">Guid</span></span>|  
|<span data-ttu-id="4d3ad-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="4d3ad-595">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-595">Int64</span></span>|  
|<span data-ttu-id="4d3ad-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4d3ad-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="4d3ad-597">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-597">Int64</span></span>|  
|<span data-ttu-id="4d3ad-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="4d3ad-599">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-599">Int32</span></span>|  
|<span data-ttu-id="4d3ad-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="4d3ad-601">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-601">Int16</span></span>|  
|<span data-ttu-id="4d3ad-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="4d3ad-603">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-603">Int64</span></span>|  
|<span data-ttu-id="4d3ad-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="4d3ad-605">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-605">String</span></span>|  
|<span data-ttu-id="4d3ad-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="4d3ad-607">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-607">String</span></span>|  
|<span data-ttu-id="4d3ad-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="4d3ad-609">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-609">String</span></span>|  
|<span data-ttu-id="4d3ad-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="4d3ad-611">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-611">String</span></span>|  
|<span data-ttu-id="4d3ad-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="4d3ad-613">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-613">String</span></span>|  
|<span data-ttu-id="4d3ad-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-614">COLLATION_NAME</span></span>|<span data-ttu-id="4d3ad-615">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-615">String</span></span>|  
|<span data-ttu-id="4d3ad-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="4d3ad-617">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-617">String</span></span>|  
|<span data-ttu-id="4d3ad-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="4d3ad-619">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-619">String</span></span>|  
|<span data-ttu-id="4d3ad-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-620">DOMAIN_NAME</span></span>|<span data-ttu-id="4d3ad-621">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-621">String</span></span>|  
|<span data-ttu-id="4d3ad-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-622">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-623">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="4d3ad-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="4d3ad-624">Procedures</span></span>  
  
|<span data-ttu-id="4d3ad-625">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-625">ColumnName</span></span>|<span data-ttu-id="4d3ad-626">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="4d3ad-628">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-628">String</span></span>|  
|<span data-ttu-id="4d3ad-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-630">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-630">String</span></span>|  
|<span data-ttu-id="4d3ad-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="4d3ad-632">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-632">String</span></span>|  
|<span data-ttu-id="4d3ad-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4d3ad-634">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-634">Int16</span></span>|  
|<span data-ttu-id="4d3ad-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="4d3ad-636">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-636">String</span></span>|  
|<span data-ttu-id="4d3ad-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-637">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-638">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-638">String</span></span>|  
|<span data-ttu-id="4d3ad-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-639">DATE_CREATED</span></span>|<span data-ttu-id="4d3ad-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-640">DateTime</span></span>|  
|<span data-ttu-id="4d3ad-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-641">DATE_MODIFIED</span></span>|<span data-ttu-id="4d3ad-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="4d3ad-643">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="4d3ad-643">Views</span></span>  
  
|<span data-ttu-id="4d3ad-644">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-644">ColumnName</span></span>|<span data-ttu-id="4d3ad-645">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-646">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-647">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-647">String</span></span>|  
|<span data-ttu-id="4d3ad-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-649">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-649">String</span></span>|  
|<span data-ttu-id="4d3ad-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-650">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-651">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-651">String</span></span>|  
|<span data-ttu-id="4d3ad-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="4d3ad-653">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-653">String</span></span>|  
|<span data-ttu-id="4d3ad-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-654">CHECK_OPTION</span></span>|<span data-ttu-id="4d3ad-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-655">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-656">IS_UPDATABLE</span></span>|<span data-ttu-id="4d3ad-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-657">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-658">DESCRIPTION</span></span>|<span data-ttu-id="4d3ad-659">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-659">String</span></span>|  
|<span data-ttu-id="4d3ad-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-660">DATE_CREATED</span></span>|<span data-ttu-id="4d3ad-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-661">DateTime</span></span>|  
|<span data-ttu-id="4d3ad-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-662">DATE_MODIFIED</span></span>|<span data-ttu-id="4d3ad-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="4d3ad-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="4d3ad-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="4d3ad-664">Indexes</span></span>  
  
|<span data-ttu-id="4d3ad-665">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4d3ad-665">ColumnName</span></span>|<span data-ttu-id="4d3ad-666">DataType</span><span class="sxs-lookup"><span data-stu-id="4d3ad-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4d3ad-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-667">TABLE_CATALOG</span></span>|<span data-ttu-id="4d3ad-668">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-668">String</span></span>|  
|<span data-ttu-id="4d3ad-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="4d3ad-670">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-670">String</span></span>|  
|<span data-ttu-id="4d3ad-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-671">TABLE_NAME</span></span>|<span data-ttu-id="4d3ad-672">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-672">String</span></span>|  
|<span data-ttu-id="4d3ad-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4d3ad-673">INDEX_CATALOG</span></span>|<span data-ttu-id="4d3ad-674">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-674">String</span></span>|  
|<span data-ttu-id="4d3ad-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="4d3ad-676">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-676">String</span></span>|  
|<span data-ttu-id="4d3ad-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-677">INDEX_NAME</span></span>|<span data-ttu-id="4d3ad-678">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-678">String</span></span>|  
|<span data-ttu-id="4d3ad-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="4d3ad-679">PRIMARY_KEY</span></span>|<span data-ttu-id="4d3ad-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-680">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-681">UNIQUE</span></span>|<span data-ttu-id="4d3ad-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-682">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="4d3ad-683">CLUSTERED</span></span>|<span data-ttu-id="4d3ad-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-684">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-685">TYP</span><span class="sxs-lookup"><span data-stu-id="4d3ad-685">TYPE</span></span>|<span data-ttu-id="4d3ad-686">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-686">Int32</span></span>|  
|<span data-ttu-id="4d3ad-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="4d3ad-687">FILL_FACTOR</span></span>|<span data-ttu-id="4d3ad-688">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-688">Int32</span></span>|  
|<span data-ttu-id="4d3ad-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-689">INITIAL_SIZE</span></span>|<span data-ttu-id="4d3ad-690">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-690">Int32</span></span>|  
|<span data-ttu-id="4d3ad-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-691">NULLS</span></span>|<span data-ttu-id="4d3ad-692">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-692">Int32</span></span>|  
|<span data-ttu-id="4d3ad-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="4d3ad-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="4d3ad-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-694">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-695">AUTO_UPDATE</span></span>|<span data-ttu-id="4d3ad-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-696">Boolean</span></span>|  
|<span data-ttu-id="4d3ad-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-697">NULL_COLLATION</span></span>|<span data-ttu-id="4d3ad-698">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-698">Int32</span></span>|  
|<span data-ttu-id="4d3ad-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="4d3ad-700">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-700">Int64</span></span>|  
|<span data-ttu-id="4d3ad-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4d3ad-701">COLUMN_NAME</span></span>|<span data-ttu-id="4d3ad-702">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-702">String</span></span>|  
|<span data-ttu-id="4d3ad-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-703">COLUMN_GUID</span></span>|<span data-ttu-id="4d3ad-704">Guid</span><span class="sxs-lookup"><span data-stu-id="4d3ad-704">Guid</span></span>|  
|<span data-ttu-id="4d3ad-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="4d3ad-705">COLUMN_PROPID</span></span>|<span data-ttu-id="4d3ad-706">Int64</span><span class="sxs-lookup"><span data-stu-id="4d3ad-706">Int64</span></span>|  
|<span data-ttu-id="4d3ad-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="4d3ad-707">COLLATION</span></span>|<span data-ttu-id="4d3ad-708">Int16</span><span class="sxs-lookup"><span data-stu-id="4d3ad-708">Int16</span></span>|  
|<span data-ttu-id="4d3ad-709">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="4d3ad-709">CARDINALITY</span></span>|<span data-ttu-id="4d3ad-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="4d3ad-710">Decimal</span></span>|  
|<span data-ttu-id="4d3ad-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="4d3ad-711">PAGES</span></span>|<span data-ttu-id="4d3ad-712">Int32</span><span class="sxs-lookup"><span data-stu-id="4d3ad-712">Int32</span></span>|  
|<span data-ttu-id="4d3ad-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="4d3ad-713">FILTER_CONDITION</span></span>|<span data-ttu-id="4d3ad-714">String</span><span class="sxs-lookup"><span data-stu-id="4d3ad-714">String</span></span>|  
|<span data-ttu-id="4d3ad-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="4d3ad-715">INTEGRATED</span></span>|<span data-ttu-id="4d3ad-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="4d3ad-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d3ad-717">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d3ad-717">See also</span></span>
- [<span data-ttu-id="4d3ad-718">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4d3ad-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
