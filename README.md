### [👉👉👉♥♥点此进入♥观看入口👈👈👈](http://a.d44k.cc/91.html)
<br></br><br></br><br></br>
        # 计算每日收益率
        returns = prices.pct_change().dropna()
        
        indicators = {
            'average_return': returns.mean(),
            'return_volatility': returns.std(),
            'sharpe_ratio': returns.mean() / returns.std(),
            'max_return': returns.max(),
            'min_return': returns.min(),
            'cumulative_return': (prices.iloc[-1] / prices.iloc[0] - 1) * 100
        }
        
        return indicators
    
    def save_results(self, results, file_path, file_type='csv'):
        """
        保存结果到文件
        参数:
            results: 要保存的结果 (DataFrame或字典)
            file_path: 文件路径
            file_type: 文件类型 ('csv' 或 'excel')
        """
        try:
            if isinstance(results, dict):
                # 如果是字典，转换为DataFrame
                results_df = pd.DataFrame.from_dict(results, orient='index')
            elif isinstance(results, pd.DataFrame):
                results_df = results
            else:
                print("不支持的结果类型，请使用字典或DataFrame")
                return False
            
            if file_type == 'csv':
                results_df.to_csv(file_path)
            elif file_type == 'excel':
                results_df.to_excel(file_path)
            else:
                print("不支持的文件类型，请使用'csv'或'excel'")
                return False
            
            return True
        except Exception as e:
            print(f"保存结果时出错: {e}")
            return False
