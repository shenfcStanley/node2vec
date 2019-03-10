Reference:

node2vec: Scalable Feature Learning for Networks.
Aditya Grover and Jure Leskovec.
Knowledge Discovery and Data Mining, 2016.

https://github.com/aditya-grover/node2vec

https://github.com/lucashu1/link-prediction


updating node2vec from python 2 to python 3:

1. In node2vecLinkPred.py, change "walks = [map(str, walk) for walk in walks]" to "walks = [list(map(str, walk)) for walk in walks]"

2. In generateGraphPickle.py, 

     2.1 we can read_edgelist directly using "edges_dir" rather than open it to a file:  
      g = nx.read_edgelist(edges_dir)

     2.2 features_series.as_matrix() --> features_series.values

     2.3 df = pd.read_table(feats_dir, sep=' ', header=None, index_col=0)  -->  df = pd.read_csv(feats_dir, sep=' ', header=None, index_col=0)

     2.4 features[i, :] = g.node[node]['features']  -->  

   try:
            features[i, :] = g.node[node]['features']
        except Exception as e:
            print
            repr(e)
            
   Otherwise, Keyerror message will show up.
